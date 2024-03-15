# Routes

## Web frontend

If a web frontend is provided, it should live at the root directory of the app: `/`.

## Resources

Resources provided by the server shall be served under `/api/v1/res/<UUID>` with the `UUID` containing to a UUID adhering to [RFC 4122](https://www.ietf.org/rfc/rfc4122.txt) of the network working group. Its version should be 4 (randomized UUID). Resources may be used for different pruposes to serve user-generated content such as profile pictures.

## Graphql

The route `/api/v1/graphql` shall correspond to the Graphql endpoint. It must respond to `POST` requests.