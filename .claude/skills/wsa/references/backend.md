# Professional Backend & Database Architecture

This guide defines the senior-level patterns required for full-stack agency delivery. These principles apply regardless of the specific stack (SQL, NoSQL, Serverless, or Monolith).

## 1. Database Modeling (Professional Integrity)

### Schema Design Principles
- **Normalization vs. Performance**: Aim for 3NF (Third Normal Form) for integrity, but denormalize strategically for high-read performance in high-aura UI.
- **Type Safety**: Use strictly typed schemas (Prisma, Zod, SQL DDL). Avoid "magic" JSON columns unless for raw logging.
- **Transactional Safety**: All multi-step operations (e.g., Payment + Order Creation) MUST be wrapped in transactions or idempotent safeguards.

### Data Migrations
- Never perform ad-hoc schema changes. All changes must be versioned migrations tracked in Git.
- Always include "Down" migrations for rollback safety.

---

## 2. API Contract-First Design

### Validation Layer
- **Zod/JSON Schema**: Use a strict validation layer at the edge of every API route. 
- Never trust client-side data. Sanitization is non-negotiable.

### Hardening Patterns
- **API Rate Limiting**: Implement per-user or per-IP limiting on all public routes.
- **Auth Guards**: Use standardized middleware for `isAuthenticated` and `hasRole` checks.
- **Error Handling**: Standardize error responses (e.g., `{ error: { code, message, field } }`). Never leak stack traces to the frontend.

---

## 3. Business Logic Isolation (The "Service" Layer)

- Keep controllers/routes thin.
- Execute business logic in isolated "Services" or "Actions." This allows for easier unit testing and future portability.

---

## 4. Integration Excellence

### Webhooks (Async Integrity)
- Handle webhooks (Stripe, Resend, CMS) with cryptographic signature verification.
- Use a persistent task queue if the processing takes >1 second to avoid timeouts.

### Environment Management
- Strict separation of `development`, `staging`, and `production` environments.
- Use a secret manager; NEVER commit `.env` or any secret keys to Git.
