---
description: >-
  The following code examples demonstrate the built-in awaitable type offered by
  the language. See section [TBD] for details.
---

# Awaitables

## Type Declaration

```
Specific Awaitable Name: Awaitable.
```

```
`Declare an awaitable that can (optionally) only contain the specified types.`

Constrained Awaitable Name A: <Context A, Context B>.
Constrained Awaitable Name B: <Context A, Context B, Context B>.
```

## Operators

### Await

```
await some awaitable,
```

```
await <some context, some awaitable>,
```

### Difference (Remove Elements)

```
<context a, context b> - <context b, context c> = <context a>
```

### Intersection

```
<context a, context b> % <context b, context c> = <context b>
```

### Union (Appending)

```
<context a, context b> + <context b, context c> = <context a, context b, context c>
```

## As Variables

### Assignment

```
some awaitable is <context a, context b>,
```

```
some awaitable is <context a, context b> + <context b, context c>,
```

```
some nested awaitable is <context a, <context b, context c>>
```

### Declaration

```
some awaitable: Awaitable [context a, context b];
```

```
specific awaitable: Specific Awaitable Name [context a, context b];
```

```
constrained awaitable: Constrained Awaitable Name A [context a];
```

```
constrained awaitable: Constrained Awaitable Name A [context a, context b];
```

```
some awaitable: Awaitable [<context a, context b> + <context b, context c>];
```

```
some nested awaitable: Awaitable [context a, some awaitable];
```

```
some awaitable: var [<context a, context b>];
```
