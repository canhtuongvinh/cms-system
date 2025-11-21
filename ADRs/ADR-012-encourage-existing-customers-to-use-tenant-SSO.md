# ADR-012: Encourage Existing Customers To Use Tenant SSO

## Context

Some consumers already hold a customer account with the tenant.  
Signing in with tenant SSO helps tenant's staffs identify the consumer faster, reduces manual verification and shortens complaint resolution time.  
A possible issue is duplicate identities. A consumer might sign in with SSO once, then create a local CMS account later using the same email or phone number. 
-> This leads to split history and slower service.

## Decision

During login, the CMS checks whether the email or phone number entered for a local CMS account already exists in the tenant’s scope.  
If the details match a record that previously authenticated through the tenant SSO, CMS concludes that the consumer is already an existing customer.  
CMS prompts the consumer to sign in using tenant SSO instead of creating or using a duplicate local account.  
If the consumer confirms the match, CMS links both records and guides future logins through SSO to maintain a single identity.

## Consequences

**Positive**
- Reduces duplicates for consumers who already belong to the tenant.  
- Speeds up complaint handling because staff can immediately identify the consumer through SSO attributes.  
- Improves data quality and complaint tracking.  
- Reduces confusion for consumers who accidentally create multiple accounts.

**Negative**
- Requires dependable email or phone matching across CMS and tenant identity records.  
- Linking flows must be simple so consumers do not get blocked during login.
