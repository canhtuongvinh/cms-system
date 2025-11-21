# ADR-007: Use Schema-Based Multi Tenancy

## Context

The CMS stores structured complaint data for many tenants. A simple shared table with tenant_id (row context) increases index size and slows queries under scale. 
A schema per tenant improves clarity and reduces index growth. This approach also supports straightforward data backup and redundancy planning.

## Decision

Use one schema per tenant in each PostgreSQL database. Each schema contains its own set of tables for complaints, logs, notes, and attachments. 
During onboarding, tenants with extreme volume or local regulatory demands may choose to separate their database. This option is offered as a higher tier and assessed case by case.

## Consequences

**Positive:**
- Smaller indexes.
- Simple debugging for each tenant.
- Clear separation of workloads.
- Flexibility for high volume or regulated tenants.

**Negative:**
- More schema management.
- Additional cost and complexity when tenants require their own database.
- Further configurations might take more time to deploy.
