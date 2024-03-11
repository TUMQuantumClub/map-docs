# Authentification

Marauder's map uses [JWTs](https://jwt.io/) to authenticate users.

## Usage

A JWT token can be aquired using the `POST /token` endpoint (TODO: link / more details on required fields). On all requests requiring authentification, the token must be sent in the HTTP `Authorization` header field.

## Structure
### Header

```json
{
  "alg": "RS512",
  "typ": "JWT"
}
```

The header is constant for all tokens. The `RSA 512-bit` algorithm shall be used by all authenticators. Otherwise, the token will be rejected.

### Payload

```json
{
  "sub": <user_id>,
  "iss": <client_id>,
  "iat": <timestamp>,
  "exp": <timestamp>
}
```

The `sub` field is required and holds a unique identifier for the user in the form of a string containing a UUID adhering to [RFC 4122](https://www.ietf.org/rfc/rfc4122.txt) of the network working group. Its version should be 4 (randomized UUID) for user ids.

The `iss` field is required and holds a unique identifier for each authrization server. It must be a string but the exact value may differ between implementations. An authorization server must always use the same `iss` value. When verifying a JWT from a client, a server must examine the `iss` field and check that the signature field matches a public key assosciated with the issuer.

All timestamp values shall be JSON-compliant integers and represent the number of __seconds__ since the Unix epoch on 1 January 1970.

The `iat` and `exp` fields are required. The `iat` field (issued at1) shall be set the the time of issuing the token by the server. The `exp` field (expiration time) must be greater than the `iat` field.

### Signature

All tokens must be signed using a `RSA 512-bit` private key that is assosciated with the `iss` field.
