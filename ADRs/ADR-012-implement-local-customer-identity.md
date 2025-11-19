# ADR 012: Implement Local Customer Identity

## Context

Some consumers (one that would like to make a claim against the tenant) are not customers of the tenant.  
They still need to submit and track complaints.  

Example: Andy saw Virgin Media carrying out maintenance and the noise affected his family well-being and wants to submit a claim, but since he is not a Virgin Media customer. 
An IdP-only sign-in approach would stop him from doing that, so the approach does not fit this use case.

CMS needs a secure local authentication method for consumers where no tenant IdP is available.

## Decision

CMS allows consumer to create accounts scoped per tenant.  
CMS stores only password hashes and salts using industry-standard algorithms.  
*No plain text passwords are stored.*
Local accounts allow any member of the public to log in, submit complaints and track updates.

## Consequences

**Positive**
- Works for tenants with no customer IdP.  
- Supports consumers who are not registered customers.  
- CMS keeps full control of password security.  
- Only hashes are stored, reducing breach impact.

**Negative**
- CMS must manage password policies and lockout rules.  
- Tenants must decide whether to enable or disable this option during onboarding.
