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