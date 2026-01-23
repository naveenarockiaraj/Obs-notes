Auth0
OIDC (OpenID Connect)
API gateway math
Python(Fast API) (PyDantic) (SqlAlchemy) (Unittest) 
UI (Nest.js) (React.js)

OIDC - Authorized permissions- connected two applications - access token and refresh token
Resource Server - 

keycloak - for authorized permissions, resource access time handle, policies.
UMA ticket - user management access ticket

Fontusapi for our RA authoried permissions provide like endpoints.
	- keycloak manage or handle the API call endpoints like who is allowed for this Endpoint

### Normal(current) flow for device access:
Org admin >>>> create access user and mapped the access user to a group to access the device.

## Customer ask
reference link: 
Keycloak Authorization Server-[https://www.keycloak.org/docs/latest/authorization_services/index.html#_policy_overview](https://www.keycloak.org/docs/latest/authorization_services/index.html#_policy_overview)

UMA 2.0 - [https://docs.kantarainitiative.org/uma/wg/rec-oauth-uma-grant-2.0.html](https://docs.kantarainitiative.org/uma/wg/rec-oauth-uma-grant-2.0.html)[https://en.wikipedia.org/wiki/User-Managed_Access](https://en.wikipedia.org/wiki/User-Managed_Access)

- Demonstrated how the authz for http(s) device access using Group Based polices.
- Demonstrated how the device access without group mapping and directly map to user using User based policies.
without mapped to any group but the user have to access the device
	for this scenario there are many policies are there
	 - user based policy
	 - role based policy
	 - JavaScript policy
	 - time based policy
	 - aggregated policy 
	 - client based policy
	 - group based policy 
	 -Client scope-based policy
	- Regex-Based Policy
    - Positive and negative logic
    -  Policy evaluation API
    - 
User based access - without resourceId(connection) - keycloak - Create the policies - goto clientID - authorization - policies - type = user - add that user policies ===> API response was allowed (TRUE)


