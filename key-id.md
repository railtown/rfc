# Key ID

In some applications, we leave it up to the host to designate their own unique identifier.

However, this poses numerous security risks. A salient one of which is that a host can easily impersonate another.

A solution to this problem is to use public keys to represent a unique ID, and have the associated private key be used to verify the authenticity of a specific host (note: the private key is known by no-one other than the host in question!).

However, the asymmetric signature scheme used can change over time, and ideally, we should version which scheme that is being used.

This document highlights the format to represent the unique identifier.

## 1 Use Case

The key ID standard will be useful for applications that has each host generate their own asymmetric key pair, and that a representation of the public key can be used as a unique ID.

With that said, this standard does not describe how an application will implement signing and verification. So in theory, the Key ID standard can be used for applications that have a centrally-generated unique ID, and centrally-verified unique IDs, with no associated private key involved.

## 2 ID Versioning

This document does not dictate what each version will represent. Versioning will lie squarely on the application implementing the Key ID scheme.

## 3 Format

The key format is defined by the following [EBNF grammar](https://datatracker.ietf.org/doc/html/rfc5234):

```
key       = version, "$", payload
payload   = any UTF-8 string
version   = "v", numbering
numbering = number, { "." number }
number    = digit, { digit }
digit     = "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"
```

In a typical application, the `payload` is what will contain the public key.

Example:

```
v1$+/drX/vc8TE=
```
