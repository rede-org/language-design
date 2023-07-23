---
description: >-
  The following code examples demonstrate how crashes can be initiated. See
  section [TBD] for details.
---

# Crashes

## Message-Only

```
crash "Some Error Message!"
```

## With Context Handling

```
`Attempt to recover with the specified operable.`

crash "Some Error Message!" for <some context, other context>
```

```
`Attempt to recover with the specified operable.`

crash "Some Error Message!" for some operable
```
