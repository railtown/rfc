# KIDV1

If an application were to use the [Key ID](key-id.md) standard, what will one of the versions represent?

This document proposes KIDV1, an implementation of the Key ID standard.

## 1.1 ES256

KIDV1 will use the [ES256](https://ldapwiki.com/wiki/ES256) signing scheme.

## 1.2 Key Format

Since ECDSA requires an `x` and `y` components, those will need to be concatenated into the final string. For the secp256r1 curve (as used in ES256), the x and y components will each span 32-bytes of data. But, as a standard, the final key will be a 65-byte string, consisting of three parts:

1. an 8-bit integer reprsenting the number `4`
2. a 32-byte value representing the `x` coordinate
3. a 32-byte value representing the `y` coordinate

## 1.3 ID Format

The ID format will follow that of [Section 3 of the Key ID standard](key-id.md#3-format), except that the `payload` will be the 65-byte key (as described in [1.2 Key Format](12-key-format)), but [base64-encoded](https://ldapwiki.com/wiki/Base64).

The version number can be whatever the application decides. The purpose of this document is not to define the version number, but instead to merely define the payload format.
