# ADR-004: Use Independent Portals Per Organisation

## Context

The CMS supports multiple organisations. Each requires its own domain, customer accounts, branding, SSO setup, workflows, chatbot, and database. A shared global identity layer would add complexity and reduce flexibility. The system needs simple horizontal scaling, strong data isolation, and clear tenant autonomy.

## Decision

Provide each organisation with an independent portal under its own domain, for example cms.natwest.com or cms.vodafone.com. Each portal runs its own configuration, identity setup, database, and optional features. This approach isolates tenants, supports growth, and aligns with consumer behaviour where users engage with one provider at a time.

## Consequences

**Positive:**

- Strong data isolation.
- Straightforward scaling.
- Autonomy for tenants to deploy features such as an AI chatbot.
- Clear branding for consumers.

**Negative:**

- More environments to manage.
