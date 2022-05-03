# n-byte base64 key ID

If an application were to use the [Key ID](key-id.md) standard, what will one of the versions represent?

This document proposes

## 1 ID Format

The ID format will follow that of [Section 3 of the Key ID standard](key-id.md#3-format), except that the `payload` will be an n-byte binary data, all base64-encoded. The value `n` represents a positive integer.
