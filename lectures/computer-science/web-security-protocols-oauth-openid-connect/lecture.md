# Web Security Protocols: OAuth, OpenID Connect

## OAuth

OAuth (Open Authorization) is an open standard for access delegation. It's used for granting apps access to user information from another service, without sharing the user's password.

There are two versions of OAuth:

- **OAuth 1.0**: Requires client applications to digitally sign requests. 

- **OAuth 2.0**: Doesn't require digital signatures, simplifying the client-side requirements.

Let's look at an OAuth 2.0 example:

```python
import requests
auth_url = "https://provider.com/o/oauth2/auth"
token_url = "https://provider.com/o/oauth2/token"
redirect_uri = "https://client.com/callback"
client_id = "<CLIENT_ID>"
client_secret = "<CLIENT_SECRET>"
# Step 1: Get authorization code
auth_response = requests.get(auth_url, params={
    "response_type": "code",
    "client_id": client_id,
    "redirect_uri": redirect_uri,
    "scope": "read"
})
# Step 2: Exchange authorization code for access token
token_response = requests.post(token_url, data={
    "code": auth_response.json()["code"],
    "client_id": client_id,
    "client_secret": client_secret,
    "redirect_uri": redirect_uri,
    "grant_type": "authorization_code"
})
access_token = token_response.json()["access_token"]
```

## OpenID Connect

OpenID Connect (OIDC) is a layer built on top of OAuth 2.0, adding user authentication to the protocol. It allows clients to verify the identity of the end-user based on the authentication performed by an authorization server.

OIDC introduces a new token type: the ID token. This is a JSON Web Token (JWT), containing user profile information (like the user's name, email, and so forth).

Here's an example of how to decode and verify an ID token:

```python
import jwt
id_token = "<ID_TOKEN>"
public_key = "<PUBLIC_KEY>"
# Decode and verify ID token
decoded_token = jwt.decode(id_token, public_key, algorithms=["RS256"])
# Print user information
print(decoded_token)
```

In this example, the `public_key` would usually be obtained from the OIDC provider's JWKS (JSON Web Key Set) endpoint.