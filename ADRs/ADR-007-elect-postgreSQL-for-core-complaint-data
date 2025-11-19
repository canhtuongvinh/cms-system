# ADR-007: Select PostgreSQL for Core Complaint Data

## Context

Complaint records have strict structure and strong links. Each complaint connects to logs, notes, attachments, customers, and staffID. The CMS needs atomic updates, joins, and audit trails. The data model fits a relational engine.

## Decision

Use PostgreSQL for core complaint data. PostgreSQL supports transactions, indexing, foreign keys, and reliable joins for structured records.

## Consequences

**Positive:**
- Strong consistency.
- Good support for audit logging.
- Reliable joins for linked complaint data.

**Negative:**
- Less suitable for flexible or irregular data.
