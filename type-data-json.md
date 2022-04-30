# JTD

This document builds on the idea of the [Type/Data Message](type-data.md), and formalizes for JSON. How a Type/Data Message can be represented in JSON should in theory not be set in stone. However, hosts in different applications will need to agree upon a standard, and JTD is one such standard that applications can rely on.

## 1 The Standard

A JTD message is a JSON object with the following fields:

- `type`: a string representing the type that the message represents
- `data`: an optional field containing the data

There really is nothing else to it.

Example:

```json
{
  "type": "CREATE_POST",
  "data": {
    "title": "Hello, World!"
  }
}
```
