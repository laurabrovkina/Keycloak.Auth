### Keycloak.Auth
* Set up Keycloak using admin in UI, go to [link](http://localhost:18080/admin/master/console/#/keycloak-auth-demo)
* Log in swagger UI:
    * User: auth@demo.com
    * Password: 12345
* If we parse the jwt token, pay an attention to an issuer and audience:
```
  "iss": "http://localhost:18080/realms/keycloak-auth-demo",
  "aud": "account",
```
Important: We need to call service inside docker, that's why MetadataAddress should look like:
```
    "MetadataAddress": "http://host.docker.internal:18080/realms/keycloak-auth-demo/.well-known/openid-configuration",
```

### Response Example
When calling `users/me` endpoint, expected response for the valid and active jwt token:
```
{
  "exp": "1768955528",
  "iat": "1768954628",
  "auth_time": "1768953762",
  "jti": "onrtna:9fc4a7b5-e580-dd4d-25bf-a138863564ee",
  "iss": "http://localhost:18080/realms/keycloak-auth-demo",
  "aud": "account",
  "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier": "bc9cf4eb-47a8-4074-8729-4a36d33d6b9a",
  "typ": "Bearer",
  "azp": "public-client",
  "sid": "yH4Lx466VkDR6DyMxDs0k8-J",
  "http://schemas.microsoft.com/claims/authnclassreference": "0",
  "allowed-origins": "https://localhost:5001",
  "realm_access": "{\"roles\":[\"offline_access\",\"uma_authorization\",\"default-roles-keycloak-auth-demo\"]}",
  "resource_access": "{\"account\":{\"roles\":[\"manage-account\",\"manage-account-links\",\"view-profile\"]}}",
  "scope": "openid profile email",
  "email_verified": "false",
  "name": "Demo Demo",
  "preferred_username": "auth@demo.com",
  "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname": "Demo",
  "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname": "Demo",
  "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress": "auth@demo.com"
}
```