---
description: >-
  The following code examples demonstrate how an operation can be declared and
  used. See section [TBD] for details.
---

# Operations

## General Declaration

```
`Defines an operation to be performed for an operable with a Context A and 
    a Context B, internally named 'context a' and 'context b', respectively.`

Some example operation for Context A and Context B: 
    <context a, context b>?
        `Operation logic.`
```

```
`Defines an operation where 'context b' will be defaulted with the specified 
    values if it is not provided as part of the operable.`

Some defaulted example operation for Context A and Context B: 
    <context a, context b [A[0], B[""]]>?
        `Operation logic.`
```

### Circumstantial Control Flow

```
`The operation will only be performed when the encapsulating application/behavior 
    is being initialized.`

An initialization operation with Context A: <context a>,
    when initialized?
        `Operation logic.`
```

```
`The operation will only be performed if no other operations within the same 
    encapsulation and matching the same operable signature (<context a>) will 
    be performed.`

Some other operation with Context A: <context a>,
    when default?
        `Operation logic.`
```

### Data Control Flow

```
`The operation will only be performed when the bucket has the required element 
    to be assigned as 'item' for the operation's internal use.`

Some example operation for {*Context A*}: <bucket>,
    where item is bucket(0)?
        `Operation logic.`
```

```
`The operation will only be performed when context a has the required mutualist 
    to be assigned as 'mutualist' for the operation's internal use.`

Some example operation for Context A: <context a>,
    where mutualist is context a (mutualist a)?
        `Operation logic.`
```

```
`The operation will only be performed when context a has the required host 
    to be assigned as 'host' for the operation's internal use.`

Some example operation for Context A: <context a>,
    where host is context a (host a)?
        `Operation logic.`
```

```
`The operation will filter 'contexts' to two new buckets for internal use 
    and will only be performed if those buckets both have at least one context.`

Update {*Context A*}: <contexts>,
    where positive contexts is contexts filtered by [(a) => a(Value A) > 0],
    where negative contexts is contexts filtered by [(a) => a(Value A) < 0],
    when |positive contexts| > 0 and |negative contexts| > 0?
    
    `Operation Logic.`
```

```
`The operation will only be performed for every value in context a' some list.`

Some example operation for Context A: <context a>,
    foreach value in context a (some list)?
        `Operation logic.`
```

```
`The operation will sort 'contexts' for two new buckets for internal use.` 

`Sort for an Operation.`
Update {*Context Type*}: <contexts>,
    where ordered contexts is contexts sorted by [(a, b) => a - b],
    where reversed contexts is contexts sorted by [(a, b) => b - a]?
    
    `Operation Logic.`
```

### Evaluative Control Flow

```
`The opeation will only be performed when context a's value a is more than 0 and 
    when context b's 'is valid' qualifier returns true.`

Some example operation for Context A and Context B: 
    <context a, context b>,
    when context a (value a) > 0, 
    when context b is valid?
        `Operation logic.`
```

```
`The operation will be performed for as long as context a's value a is more than 0 
    and when context b's 'is valid' qualifier returns true.`

Some example operation for Context A and Context B: 
    <context a, context b>,
    while context a (value a) > 0,
    when context b is valid?
        `Operation logic.`
```

### Reactive Control Flow

```
`The operation will be performed, during a reactive evaluation cycle of the 
    application, whenever context a's value a is more than 0.`

Some example operation for Context A and Context B: 
    <context a, context b>,
    whenever context a (value a) > 0?
        `Operation logic.`
```

```
`The operation will be performed continuously, during a reactive evaluation cycle 
    of the application, for as long as context a's value a is more than 0.`

Some example operation for Context A and Context B: 
    <context a, context b>,
    whilever context a (value a) > 0?
        `Operation logic.`
```

## Identification-Based Declarations

### With Identifier

```
Some Example Operation :: Some example operation for Context A and Context B: 
    <context a, context b>?
        `Operation logic.`
```

### Relational Control Flow

```
`The operation will be performed after 'Another Identified Operation', regardless of 
    whether that operation has actually been performed.`

Some example operation for Context A and Context B: 
    <context a, context b>,
    after Another Identified Operation?
        `Operation logic.`
```

```
`The operation will be performed before 'Another Identified Operation', regardless 
    of whether that operation will actually be performed.`

Some example operation for Context A and Context B: 
    <context a, context b>,
    before Another Identified Operation?
        `Operation logic.`
```

```
`The operation will be performed after 'Another Identified Operation', and only 
     if that operation has actually been performed.`

Some example operation for Context A and Context B: 
    <context a, context b>,
    only after Another Identified Operation?
        `Operation logic.`
```

```
`The operation will be performed before 'Another Identified Operation', and only 
    if that operation will actually be performed.`

Some example operation for Context A and Context B: 
    <context a, context b>,
    only before Another Identified Operation?
        `Operation logic.`
```

### Replacements

```
`Replacement operations supercede their specified replaced operations.
    If a replacement operation qualifies, the replaced operation will 
    not be performed in favor of the replacement operation.`

Another example operation for Context A, Context B, and Context C:
    {context a, context b, context c} replaces Some Example Operation?
    
    `Operation logic.`
```

## Nested Operations

```
`TODO :: Nested operations.`
```

