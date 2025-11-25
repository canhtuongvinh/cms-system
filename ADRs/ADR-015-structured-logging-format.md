# ADR-015: Structured Logging Format

## Context
The CMS needs reliable logs to track behaviour across many tenants. Logs support debugging, security reviews, and regulatory checks. Unstructured logs make analysis slow and inconsistent, especially at scale.

## Decision
Adopt a structured JSON log format with the following fields:
- timestamp
- tenant_id
- user_id
- request_id
- service_name
- action
- outcome
- latency_ms
- error_code if present

All services write logs in this format. All logs follow UTC time.

## Consequences

**Positive:**
- Faster search and filtering
- Clear trace of actions across services
- Better alignment with audit expectations
- Simple integration with monitoring tools

**Negative:**
- Slightly higher storage use
- More detail needed when writing log entries
