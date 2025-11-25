# ADR-014: Tenant Isolation Rules

## Context
The CMS serves many organisations. Each organisation needs strict separation of data, users, and workloads. This protects customer information and supports regulatory expectations. The system design uses shared infrastructure, so isolation must be applied at the data layer and the application layer.

## Decision
Enforce tenant isolation with the following rules:
- Every request includes a tenant identifier from the authentication layer.
- Each relational query runs inside the tenant’s schema.
- Each NoSQL query filters by tenant scope.
- Each blob path uses a tenant prefix.
- Services reject cross tenant access at the API layer.

## Consequences

**Positive:**
- Clear separation of data for each organisation
- Lower risk of data leakage
- Better support for audits and compliance reviews
- Simple debugging because each tenant’s data lives in its own boundaries

**Negative:**
- Extra checks at query and API level
- More work when onboarding new tenants
