# ADR-009: Staff Identity Provider Integration

## Context

Tenant staff include help desk agents, support persons, managers and system administrators. These users belong to the tenant organisation and authenticate through the tenant’s corporate identity platform such as Azure AD, Okta.
The CMS avoids storing staff passwords to reduce risk and simplify compliance.  
Staff need controlled access to complaint data within their tenant. Each tenant must manage staff lifecycle, permissions and MFA rules.  
The system supports multi-tenant isolation and separate portals, so staff login must follow that model.

## Decision

CMS delegates all staff authentication to each tenant’s identity provider.  
Staff sign in through the tenant IdP, after authentication, the tenant IdP sends CMS a signed token with tenant_id, staff_id and role.  
CMS verifies the token, creates a session and applies role based access control.  
*CMS does not store staff passwords.*

## Consequences

**Positive**
- Tenant owns staff identity and MFA policy.  
- No password storage for staff in CMS.  
- Staff lifecycle and access removal stay under tenant control.  
- Lower operational risk and simpler audits.  
- Fits the multi tenant model described in the architecture and security sections.

**Negative**
- Each tenant must configure an IdP integration during onboarding.  
- Mapping staff roles requires coordination with the tenant identity team.
