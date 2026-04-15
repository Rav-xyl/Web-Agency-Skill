# Professional Backend & Database Architecture

This guide defines the senior-level patterns required for full-stack agency delivery. These principles apply regardless of the specific stack (SQL, NoSQL, Serverless, or Monolith).

---

## 1. Provider Discovery & Evaluation
Before implementing a third-party service, the AI must verify availability and suitability for the client's jurisdiction.

### [Checklist] Service Qualification
- **Jurisdiction**: Is the provider supported in the client's country? (e.g., Stripe vs. Razorpay vs. Adyen).
- **Compliance**: Does the provider meet local data residency laws (GDPR, CCPA, Digital Personal Data Protection Act)?
- **Currency**: Does it support the settlement currency required by the business?
- **Redundancy**: Is there a secondary provider available if the primary fails/rejects the business?

---

## 2. Database Modeling (Professional Integrity)

### Schema Design Principles
- **Normalization (3NF)**: Prioritize data integrity. Every non-key attribute must depend on the primary key, the whole key, and nothing but the key.
- **Relational Integrity**: Use Foreign Keys and Constraints at the database level. Never rely solely on application-level logic for integrity.

### [Example] Normalized E-commerce Schema (SQL)
```sql
-- Core Business Entities
CREATE TABLE customers (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    email VARCHAR(255) UNIQUE NOT NULL,
    created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

CREATE TABLE products (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    sku VARCHAR(50) UNIQUE NOT NULL,
    name VARCHAR(255) NOT NULL,
    price_cents INTEGER NOT NULL, -- Always store currency in cents
    currency CHAR(3) DEFAULT 'USD'
);

CREATE TABLE orders (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    customer_id UUID REFERENCES customers(id),
    status VARCHAR(50) NOT NULL, -- e.g., 'pending', 'paid', 'failed'
    total_cents INTEGER NOT NULL,
    idempotency_key UUID UNIQUE NOT NULL, -- Prevent double charging
    created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

CREATE TABLE order_items (
    order_id UUID REFERENCES orders(id) ON DELETE CASCADE,
    product_id UUID REFERENCES products(id),
    quantity INTEGER CHECK (quantity > 0),
    unit_price_cents INTEGER NOT NULL,
    PRIMARY KEY (order_id, product_id)
);
```

---

## 3. Agnostic Integration Patterns

### The Gateway Interface (Strategy Pattern)
Decouple business logic from specific provider SDKs.

```typescript
// Define a common interface for all payment providers
interface PaymentGateway {
  processPayment(amount: number, currency: string, source: string): Promise<PaymentResult>;
  verifyWebhook(payload: any, signature: string): boolean;
}

// Strategy 1: Stripe Adapter
class StripeAdapter implements PaymentGateway {
  async processPayment(amount: number, currency: string, source: string) {
    // Stripe specific logic
    return { success: true, transactionId: 'ch_...' };
  }
}

// Strategy 2: Razorpay Adapter (For countries where Stripe is limited)
class RazorpayAdapter implements PaymentGateway {
  async processPayment(amount: number, currency: string, source: string) {
    // Razorpay specific logic
    return { success: true, transactionId: 'pay_...' };
  }
}
```

---

## 4. API Contract-First Design (Zod Registry)
Use a centralized registry for all data entering or leaving the system.

```typescript
import { z } from 'zod';

// Agnostic Payment Request
export const PaymentRequestSchema = z.object({
  orderId: z.string().uuid(),
  amountCents: z.number().int().positive(),
  currency: z.enum(['USD', 'EUR', 'INR', 'GBP']),
  paymentMethodId: z.string().min(1),
});

// Environment Configuration Validation
export const EnvSchema = z.object({
  DATABASE_URL: z.string().url(),
  PAYMENT_PROVIDER: z.enum(['STRIPE', 'RAZORPAY', 'ADYEN']),
  WEBHOOK_SECRET: z.string().min(32),
});
```

---

## 5. Webhook Integrity (Async Guard)
Always verify signatures before processing asynchronous events.

```typescript
async function handleWebhook(req: Request) {
  const signature = req.headers.get('x-provider-signature');
  const payload = await req.text();

  // 1. Verify Source (Agnostic Wrapper)
  const isValid = gateway.verifyWebhook(payload, signature);
  if (!isValid) throw new Error("Unauthorized Webhook Source");

  // 2. Map to Internal State
  const event = JSON.parse(payload);
  const internalId = event.data.object.metadata.internal_id;

  // 3. Update State via Transaction
  await db.transaction(async (tx) => {
    const order = await tx.orders.findUnique({ where: { id: internalId } });
    if (order.status === 'paid') return; // Idempotency check
    await tx.orders.update({ where: { id: internalId }, data: { status: 'paid' } });
  });
}
```

---

## 6. Business Logic Isolation (The Service Layer)
Keep controllers thin. Logic belongs in Services.

- **Controller**: Parses request → Validates via Zod → Calls Service.
- **Service**: Executes business logic → Orchestrates Gateways → Accesses Repository.
- **Repository**: Pure data access (CRUD).

---

## 7. Performance & Hardening
- **Connection Pooling**: Use a proxy (e.g., PgBouncer) for serverless environments.
- **Circuit Breakers**: Use `resilience4j` or similar patterns for 3rd party API calls.
- **Audit Logs**: Record every state change in an `audit_logs` table for financial compliance.
