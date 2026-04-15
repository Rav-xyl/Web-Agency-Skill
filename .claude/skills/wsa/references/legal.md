# Legal Reference

## Contract — Key Clauses

Every project needs a signed contract before work begins. These are the non-negotiable clauses.

### Scope of Work
"Services are limited to the pages, features, and functionality described in the attached
Project Brief dated [date]. Any changes to scope require a written Change Request and
additional payment before implementation."

### Revision Policy
"The project includes [2] rounds of revisions. A revision round is defined as a consolidated
set of changes submitted in a single document or message. Additional rounds are billed at
[₹X / $X] per hour."

### Kill Fee
"If client cancels the project after work has begun, the following fees apply:
- Cancellation within 7 days of start: 30% of project total
- Cancellation after 25% completion: 50% of project total
- Cancellation after 50% completion: 75% of project total
Deposit is non-refundable in all cases."

### Intellectual Property
"All work product, source code, design files, and content created for this project
are owned by the client upon receipt of final payment in full. Prior to final payment,
all work remains the property of [Your Name / Agency Name]."

### Warranty
"[Your Name] warrants the delivered website against defects in code for 30 days
following launch. This warranty covers bugs present at launch only. New feature
requests, content updates, or issues caused by client modifications are not covered."

### Liability Limit
"[Your Name]'s total liability for any claim arising from this project shall not
exceed the total fees paid by the client for this project."

### Client Responsibilities
"Client is responsible for providing all content (copy, images, branding) by [date].
Delays in content delivery may delay project milestones. Client is responsible for
ensuring they have rights to all content provided."

### Post-Launch Support
"Post-launch support is not included unless a separate Maintenance Retainer Agreement
is signed. Emergency support is available at [₹X / $X] per hour."

---

## Payment Terms Template

```
Invoice terms:
- 30–50% deposit due before work begins (non-refundable)
- Remaining balance due on delivery / before production launch
- Invoices unpaid after 14 days incur 2% monthly late fee
- Final credentials and source files released only upon receipt of full payment
```

---

## GDPR Compliance (EU / UK Traffic)

Required if your client's site collects any data from EU or UK residents.

### What Triggers GDPR
- Contact forms (name, email)
- Google Analytics / any tracking cookies
- Newsletter sign-ups
- E-commerce (address, payment data)
- User accounts

### GDPR Checklist
- [ ] Privacy Policy: what data is collected, why, how long kept, who has access
- [ ] Cookie consent banner: user must opt-in to non-essential cookies (analytics, marketing)
- [ ] Data processing agreement (DPA) signed with all processors (GA4, Stripe, Mailchimp)
- [ ] Right to deletion: user can request their data be deleted — document the process
- [ ] Right to access: user can request a copy of their data
- [ ] Data breach notification plan: must notify relevant DPA within 72 hours of discovery
- [ ] No data transfer outside EU/UK without adequate safeguards (Standard Contractual Clauses)

### Google Analytics 4 + GDPR
- Enable IP anonymisation in GA4 (on by default in GA4)
- Do not enable Google Signals if you have EU users and no explicit consent
- Use a GDPR-compliant consent mode (Cookiebot, CookieYes, or Axeptio)
- Consider Plausible or Fathom as GDPR-native alternatives (no consent banner needed)

---

## CCPA (California, USA)

Required if: business targets California residents AND (annual revenue > $25M OR
processes data of 100k+ consumers/year OR earns 50%+ revenue from selling data).

### CCPA Checklist
- [ ] Privacy Policy updated with CCPA-specific language
- [ ] "Do Not Sell My Personal Information" link in footer (if data is sold/shared for ads)
- [ ] Opt-out mechanism functional
- [ ] Respond to consumer requests within 45 days

---

## India — IT Rules & Consumer Protection

### Applicable to Indian businesses / Indian users
- [ ] Privacy Policy compliant with IT (Amendment) Rules 2008
- [ ] For e-commerce: display business name, address, customer care email, GST number
- [ ] Consumer Protection (E-Commerce) Rules 2020: mandatory grievance officer contact,
      return/refund policy displayed, no fake reviews
- [ ] RBI compliance if accepting online payments: use only approved payment gateways
- [ ] DPDP Act 2023 (Digital Personal Data Protection): consent-based data processing,
      data fiduciaries must appoint a Data Protection Officer for significant data

---

## WCAG Accessibility — Legal Requirement

Accessibility is a legal requirement in multiple jurisdictions, not just a best practice.

| Jurisdiction | Law | Standard Required |
|---|---|---|
| European Union | European Accessibility Act (2025) | WCAG 2.1 AA |
| United Kingdom | Equality Act 2010 | WCAG 2.1 AA |
| United States | ADA (Americans with Disabilities Act) | WCAG 2.1 AA |
| Australia | Disability Discrimination Act | WCAG 2.1 AA |
| India | Rights of Persons with Disabilities Act 2016 | WCAG 2.0 AA |

### Minimum Compliance Checklist
- [ ] All images have descriptive alt text
- [ ] Colour contrast ≥ 4.5:1 for normal text, ≥ 3:1 for large text (check: webaim.org/resources/contrastchecker)
- [ ] All interactive elements reachable and operable by keyboard
- [ ] Focus indicators visible on all interactive elements
- [ ] Forms: all inputs have associated labels
- [ ] No content relies solely on colour to convey meaning
- [ ] Videos have captions
- [ ] Site is navigable with a screen reader (test with VoiceOver / NVDA)
- [ ] Run axe DevTools or WAVE on all pages before launch

---

## Legal Pages Every Site Needs

### Required for All Sites
- **Privacy Policy**: what data is collected, how it's used, user rights
  - Tool: Termly.io or iubenda for template generation
- **Cookie Policy** (or include in Privacy Policy): what cookies are used, why

### Required for E-Commerce
- **Terms and Conditions / Terms of Sale**
- **Refund / Return Policy**
- **Shipping Policy** (if physical goods)
- **Cancellation Policy** (if subscriptions)

### Required for SaaS / User Accounts
- **Terms of Service**
- **Acceptable Use Policy**
- **Data Processing Agreement** (if B2B and processing client data)

### Footer Requirements (Minimum)
```html
© [Year] [Business Name]. All rights reserved.
<a href="/privacy">Privacy Policy</a> · <a href="/terms">Terms</a>
[Business Address] · [GST/VAT number if applicable]
```

---

## Freelancer Legal Protection

### Before Every Project
1. Signed contract with all clauses above
2. Deposit paid and cleared
3. Scope documented in writing

### During Project
- All scope changes in writing (email is fine)
- Client approvals documented (design sign-off, QA sign-off)
- Keep all communication records

### After Project
- Final payment received before credential transfer
- Handoff sign-off document signed
- Revoke your own access after transfer
- Archive project files for minimum 2 years
