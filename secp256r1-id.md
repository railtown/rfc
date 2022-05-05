# Using a Base64-encoded NIST secp256r1 keys as client IDs

Advantages of ECDSA:

- small key sizes
- fast signing and verification
- as secure as RSA

The small key size makes ECDSA a perfect candidate as a potential blockchain-styled identifier.

Unlike Bitcoin and Ethereum, however, the base64-encoded NIST secp256r1 key will not be hashed, and instead will be sent as is. Not even the y coordinate will be omitted, even if the y coordinate can be derived from the first byte of the NIST client ID (if the first byte represents 2 or 3).

This makes actually using the client ID as a signature verifier even easier. No need of any validation, recipient-side.

## 1.1. The underlying binary format

The underlying binary format is going to follow the [NIST EC format](https://www.cryptosys.net/pki/manpki/pki_ecchexformat.html).

That is a single byte set to literally the number 4, and two 32-byte numbers, representing the numbers x and y, respectively.

So the overall key length is going to be 65 bytes.
