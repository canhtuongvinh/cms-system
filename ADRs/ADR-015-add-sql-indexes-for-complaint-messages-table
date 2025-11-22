# ADR-015: Add SQL Indexes for Complaint Messages Table

## Context

The CMS supports chat between consumers and staffs. Messages grow fast across tenants. Projections show more than 20 million messages at minimum. Queries must return threads, latest entries, and unread counts without delay. A messages table without indexes forces a full table scans. That slows reads as volume grows. This affects SLA targets and user experience.

## Decision

Add indexes to the messages table on fields used in frequent queries. These include complaint_id, tenant_id, sender_id, created_at, and visibility. This supports fast retrieval for message lists, status updates, and pagination. This keeps response times stable under heavy message volume.

## Consequences

**Positive**

- Faster reads for message threads
- Stable performance at scale
- Lower CPU load during peak hours
- Better SLA reporting
- More responsive UI

**Negative**

- Higher storage use for index structures
- Slower inserts due to index updates
- More attention needed for index maintenance

## Without Indexes

A SQL query without indexes scans all rows. Example:

```sql
SELECT *
FROM complaint_messages
WHERE complaint_id = 'ABC-123'
ORDER BY created_at DESC
LIMIT 20;
