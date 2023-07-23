---
description: >-
  The following code examples demonstrate the built-in operable type offered by
  the language. See section [TBD] for details.
---

# Operables

## Type Declaration

```
Specific Operable Name: Operable.
```

```
`Declare an operable that can only contain up to the specified types.`

Constrained Operable Name A: <Context A, Context B>.
Constrained Operable Name B: <Context A, Context B, Context B>.
```

## Operators

### Accessing

#### Containment

```
some operable: Operable [context a, context b];

`Index checks.`
some operable(0?) = true
some operable(1?, 2?) = {true, false}
```

#### Retrieving

```
some operable: Operable [context a, context b];
some operable(0) = <context a>
```

```
some operable: Operable [context a, context b];
some operable(...) = <context a, context b>  `Total collection accessor.`
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
some operable is <context a, context b, some bucket, some composition>,
```

```
some operable is <context a, context b> + <context b, context c>,
```

```
`Index-based assignment.`
some operable(0) is <context d>,
```

```
some nested operable is <context a, <context b, context c>, {context d}>,
```

### Declaration

```
some operable: Operable [context a, context b, some bucket, some composition];
```

```
specific operable: Specific Operable Name [context a, context b];
```

```
constrained operable: Constrained Operable Name A [context a];
```

```
constrained operable: Constrained Operable Name A [context a, context b];
```

```
some operable: Operable [<context a, context b> + <context b, context c>];
```

```
some nested operable: Operable [context a, some operable];
```
