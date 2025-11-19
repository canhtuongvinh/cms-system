# ADR-011: Customer SSO Authentication Integration

## Context

Some tenants might provide a customer identity provider.  
These tenants might want customers to authenticate with their existing customer accounts instead of creating new CMS credentials. This keeps customer identity inside the tenant’s control and simplifies the login flow for known customers.  
Other tenants do not provide a customer IdP, so this authentication method could be left as an option.

## Decision

CMS supports customer SSO for tenants that configure a customer IdP.  
When enabled, CMS directs the consumer to the tenant IdP, as a result the tenant IdP returns a signed token with customer_id, and other data points as emails, telephone, etc such as uniqueness.
CMS verifies the token, starts a session and assigns the consumer role.  
*CMS does not store consumer passwords for tenants using this option.*

Example: https://teksalah.com/wp-content/uploads/2020/11/Drawing1-1.jpg

## Consequences

**Positive**
- Consumers reuse an existing tenant account.  
- Tenant controls all customer policies.  
- CMS avoids password storage for these tenants.  
- Lower operational risk and simple integration for large banks and telecoms.

**Negative**
- Only works for tenants that provide a customer IdP.  
- Requires extensive setup during onboarding.
