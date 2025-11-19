# ADR 011: Customer SSO Authentication Integration

## Context

Some tenants provide a customer identity provider.  
These tenants want consumers to authenticate with their existing customer accounts instead of creating new CMS credentials.  
This keeps customer identity inside the tenant’s control and simplifies the login flow for known customers.  
Other tenants do not provide a customer IdP, so this method must remain optional.

## Decision

CMS supports customer SSO for tenants that configure a customer IdP.  
When enabled, CMS redirects the consumer to the tenant IdP using OIDC or SAML.  
The tenant IdP returns a signed token with tenant_id and customer_id.  
CMS verifies the token, starts a session and assigns the consumer role.  
CMS does not store consumer passwords for tenants using this option.

## Consequences

**Positive**
- Consumers reuse an existing tenant account.  
- Tenant controls all customer policies.  
- CMS avoids password storage for these tenants.  
- Lower operational risk and simple integration for large banks and telecoms.

**Negative**
- Only works for tenants that provide a customer IdP.  
- Requires setup during onboarding.
