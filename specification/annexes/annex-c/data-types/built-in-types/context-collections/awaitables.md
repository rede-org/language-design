---
description: >-
  The following code examples demonstrate the built-in awaitable type offered by
  the language. See section [TBD] for details.
---

# Awaitables

## Operators

### Await

```
await someAwaitable,
```

```
await <someContext, someAwaitable>,
```

### Difference (Remove Elements)

```
<contextA, contextB> - <contextB, contextC> = <contextA>
```

### Intersection

```
<contextA, contextB> % <contextB, contextC> = <contextB>
```

### Union (Appending)

```
<contextA, contextB> + <contextB, contextC> = <contextA, contextB, contextC>
```

## Variables

### Assignment

```
someAwaitable is <contextA, contextB>,
```

```
someAwaitable is <contextA, contextB> + <contextB, contextC>,
```

```
someNestedAwaitable is <contextA, <contextB, contextC>>
```

### Declaration

```
someAwaitable: awaitable, <contextA, contextB>;
```

```
someAwaitable: awaitable, <contextA, contextB> + <contextB, contextC>;
```

```
someNestedAwaitable: awaitable, <contextA, someAwaitable>;
```
