# dietapp-api-gateway

## Keycloak

## Instructions on how to configure keycloak

Available on http://localhost:8181/
After docker of keycloak is up:

1. Credential for login are described in the docker-compose
2. Create a new Realm (a new Domain in KC): **dietapp-security-realm**
3. Create a new Client, and provide an ID: "dietapp-credentials-id", and click "next"
4. Select Client Authentication: ON
5. On Authentication Flows, select **only** "Service accounts roles", then Next and Save. Client is created.
6. On the Credentials tab, you can see the client-secret (you can copy it later)
7. On the left, click Realm Settings.
8. On the bottom, next to "Endpoints", select "OpenID Endpoint Configuration" which will be opened in a new browser page
9. The "issuer" URL should be put into the field of "spring.security.oauth2.resourceserver.jwt.issuer-uri"

On Postman:

1. In Authorization tab, select OAuth 2.0
2. In "Access Token URL" put URL from keycloak which ends with "token" (should be called "token_endpoint")
3. In Client ID field put the Client ID from KC
4. In Client Secret field put the Client Secret copied from KC
5. Select "Get new access token", and afterwards "Use token"
   You should now be able to call the API Gateway endpoint.
