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

### Await

```
await some bucket,
```

```
await <some context, some bucket>,
```

### Difference (Remove Elements)

```
{*context a, context b*} - {*context b, context c*} = {*context a*}
```

### Filter

```
`Filter for a Behavior.`
Manage {*Context Type*}: {contexts},
    filter contexts by result for a:
        await <a, result as filter result>?
    
    `Behavior Operations.`
```

```
`Filter for an Operation.`
Update {*Context Type*}: <contexts>,
    positive contexts <- filter contexts by result for a:
        result is a(ValueA) > 0;
    negative contexts <- filter contexts by result for a:
        result is a(ValueA) < 0;
    when |positive contexts| > 0 and |negative contexts| > 0?
    
    `Operation Logic.`
```

### Intersection

```
{*context a, context b*} % {*context b, context c*} = {*context b*}
```

### Run

```
run some bucket,
```

```
run {*context a, context b*},
```

```
run <some context, some bucket>,
```

### Sort

```
`Sort for a Behavior.`
Manage {*Context Type*}: {contexts},
    sort contexts by result for a, b:
        await <a, b, result as sort result>?
    
    `Behavior Operations.`
```

```
`Sort for an Operation.`
Update {*Context Type*}: <contexts>,
    ordered contexts <- sort contexts by result for a, b:
        result is a(ValueA) - b(ValueA);
    reversed contexts <- sort contexts by result for a, b:
        result is b(ValueA) - a(ValueA)?
    
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
