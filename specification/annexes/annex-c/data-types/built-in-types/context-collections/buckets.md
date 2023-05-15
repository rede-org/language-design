---
description: >-
  The following code examples demonstrate the built-in bucket type offered by
  the language. See section [TBD] for details.
---

# Buckets

## Type Declaration

```
Specific Bucket Name: {*Context Type*}.
```

## Operators

### Accessing

#### Containment

```
some bucket: {*Context Type*} [context a, context b];

`Index checks.`
some bucket(1?) = true
some bucket(2?) = false

`ID checks.`
some bucket(context a id?) = true
some bucket(context c id?) = false
```

```
some bucket: {*Context Type*} [context a, context b];
some bucket(1?, context c id?) = {true, false}
```

#### Retrieving

```
some bucket: {*Context Type*} [context a, context b];
some bucket(0) = {*context a*}
some bucket(context b id) = {*context b*}
```

```
some bucket: {*Context Type*} [context a, context b];
some bucket(...) = {*context a, context b*}  `Total collection accessor.`
```

### Difference (Remove Elements)

```
{*context a, context b*} - {*context b, context c*} = {*context a*}
```

### Filter

```
`Filter for a Behavior.`
`Generic 'T' is treated as the defined type, Base Context.`
Manage {*T*} (T [Base Context]): {contexts},
    where contexts $! [(a) => a meets criteria]?
    
    `Behavior Operations.`
```

```
`Filter for an Operation.`
Update {*Context Type*}: <contexts>,
    where positive contexts is contexts &! [(a) => a(Value A) > 0],
    where negative contexts is contexts &! [(a) => a(Value A) < 0],
    when |positive contexts| > 0 and |negative contexts| > 0?
    
    `Operation Logic.`
```

### Intersection

```
{*context a, context b*} % {*context b, context c*} = {*context b*}
```

### Sort

```
`Sort for a Behavior.`
`Generic 'T' is treated as the defined type, Base Context.`
Manage {*T*} (T [Base Context]): {contexts},
    where contexts &^ [(a, b => a - b]?
    
    `Behavior Operations.`
```

```
`Sort for an Operation.`
Update {*Context Type*}: <contexts>,
    where ordered contexts is contexts &^ [(a, b) => a - b],
    where reversed contexts is contexts &^ [(a, b) => b - a]?
    
    `Operation Logic.`
```

### Union (Appending)

```
{*context a, context b*} + {*context b, context c*} = 
    {*context a, context b, context c*}
```

## As Variables

### Assignment

```
some bucket is {*context a, context b*},
```

```
some operable is {*context a, context b*} + {*context b, context c*},
```

### Declaration

```
some bucket: {*Context Type*} [context a, context b];
```

```
specific bucket: Specific Bucket Name [context a, context b];
```

```
some bucket: {*Context Type*} [{*context a, context b*} + {*context b, context c*}];
```
