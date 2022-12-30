---
description: >-
  The following code examples demonstrate how awaitables can be declared and
  used. See section [TBD] for details.
---

# Awaitables

## Type Declaration

```
awaitableName: <contextNameA, contextNameB>.
```

```
awaitableName: <contextNameA, otherAwaitableName>.
```

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
someAwaitable: awaitableName, <contextA, contextB>;
```

```
someAwaitable: var, <contextA, contextB>;  `Type determined by initialization value.`
```

```
someAwaitable: nameA + nameB, <contextA, contextB> + <contextB, contextC>;
```

```
someNestedAwaitable: var, <contextA, someAwaitable>;
```
