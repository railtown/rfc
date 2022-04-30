# Type/Data Message

An entire application would often have a single streaming connection open, where both hosts send messages to each other.

That single connection will have messages being sent, where each message will have different intentions, and can be assumed to be entirely independent from each other.

And it's for that reason that there needs to be a way to distinguish what each message will represent.

This document outlines the abstract idea of tagging a message with a single "type", and followed by the data payload.

## 1 The Idea

No need to complicate things. This idea is that applications will send a message using a data interchange format of their choice (whether it be XML, YAML, JSON, etc.), with a section of the data designated as the tag that determines what "type" the message is, and then optionally, another field used to hold the data that is in the message.
