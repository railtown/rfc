# Key ID with WebSocket

[Key ID](key-id.md)s are ideal for stateless client authentication.

Even though WebSocket (unlike HTTP) is a stateful protocol, if a WebSocket connection were to die, so will the state between client and server. Thus either the client or the server will need to host some information.

Given the nature of Key ID, the client issues a connection, and will need to identify itself. Thus, maintaining authentication information will need to lie on the client, and not the server.

This document provides

## 1 Connecting with a query parameter

## 1.1 WebSocket connection

The client MUST supply the Key ID to the server via agreed-upon query parameter. The default is `client_id`, but the server can decide on a different query parameter name, and the client needs to be aware of that ahead of time.

Example:

```
wss://example.com/ws?client_id=v1$dp1bzw5pfNE=
```

If a valid Key ID was not supplied via the query parameter, then the server will close the connection.

It is recommended that the server provides the courtesy of notifying the client that the it has not provided a valid Key ID.
