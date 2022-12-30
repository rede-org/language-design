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
crash "Some Error Message!" for <someContext, otherContext>
```

```
crash "Some Error Message!" for someAwaitable
```
