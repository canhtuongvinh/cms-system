# ADR-008: Adopt Tenant Specific Encryption Keys

## Context

The CMS stores sensitive complaint data and attachments. A single global encryption key creates risk. 
A breach could expose all tenants. Data protection laws require strong isolation.

## Decision

Generate one encryption key per tenant. Store keys in the cloud Key Management Service. Encrypt complaint data, attachments, and sensitive fields with the tenant key.

## Consequences

**Positive:**
- Limits impact of breaches.
- Supports separate key rotation.
- Fits tenant level security policies.

**Negative:**
- More keys to manage.
- Rotationally change keys might be mismatch, will require manual reconfiguration.
