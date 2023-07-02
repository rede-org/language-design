---
description: >-
  The following code examples demonstrate how a pattern can be declared and
  used. See section [TBD] for details.
---

# Patterns

## Declaration

```
Pattern Type: [matched value: int [-1]; s: string ["None"]; last value: bool].
```

## Use

```
`Define a pattern that will match a sequentially equivalent, value-equivalent 
    construct, assigning values to "matched value", "s", and "last value".`

pattern a: Pattern Type [matched value, = "Matches A", ..., s, last value];
```

```
`Define a pattern that will match a sequentially equivalent, value-equivalent 
    construct, assigning values to "matched value" and "last value".`

pattern b: Pattern Type [matched value, = "Matches B", ..., last value];
```

```
`Define a pattern that will match a sequentially equivalent, value-conforming 
    construct.`

pattern c: [] [ > 10, = "Matches C", ...];
```

```
`Define a pattern that will match a sequentially equivalent value-conforming 
    construct.`

pattern d: [] [ > 10 and < 100, ...];
```

```
`Define a pattern that will match a sequentially equivalent, value-conforming 
    construct.`

pattern e: [] [ = 100];
```

```
`Define a pattern that will match a loosely sequentially equivalent 
    construct with the specified "Some Value" value equivalent to "Matches F".`

pattern f: [s: string] [..., (Some Value) = "Matches F", 
    ..., s is (Other String), ...];
```

```
`Use a declared pattern in an operable.`

pattern a: [] [ = 100];
await <context a, pattern a>,
```

### With Mappings

```
`Declare a mapping that provides an enum value that reflects whether a list of 
    strings matches either of the specified patterns.`

{String*} matching [] or [] to Result: (list, a, b) ??
    list $ a => Result (Matches A),
    list $ b => Result (Matches B),
    default => Result (Does Not Match).
```

### With Operations

```
`Declare an operation that qualifies based on a provided pattern and 
    an anonymous pattern.`

Some operation with Context A and Pattern Type: <a, pattern>,
    when a $ pattern,
    when a $ [..., (Value C) > 10, = "Example", ...]?
        `Operation logic.`
```

