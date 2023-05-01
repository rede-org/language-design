---
description: >-
  The following code examples demonstrate how a mapping can be declared and
  used. See section [TBD] for details.
---

# Mappings

## Declaration

```
Some Record to Int: (r) => r(Value A).
```

```
Int to Some Record: (i) => {Value A [i], Value B [0]}.
```

```
Some Record to alt Int: (r) => r(Value B).
```

```
Some Record with Int to Int: (r, i) => r(Value A) + i.
```

```
Some Record to {Int, Int}: (r) => {r(Value A), r(Value B)}.
```

```
Some Record with Int to {Int, Int}: (r, i) => {r(Value A) + i, r(Value B) + i}.
```

```
{Int*} to half sum Int: (list) => $+list / 2.
```

```
{Int*} to doubled {Int*}: (list) => list $$ (i) => i * 2.
```

```
{Int*} with (Int => String) to {String*}: (list, mapping) => list $$ mapping.
```

```
Int to Some Enum: (i) ??
    i = 0 => Some Enum (A),
    i = 1 => Some Enum (B),
    i = 2 => Some Enum (C),
    default => Some Enum (A).
```

```
Some Enum to Other Enum: (e) ??
    e = A => Other Enum (X),
    e = B => Other Enum (Y),
    e = C => Other Enum (Z),
    default => Other Enum (X).
```

#### With Identifiers

```
SR to Int :: Some Record to Int: (r) => r(Value A).
```

#### With Replacements

```
Some Record to Int: (r) replaces SR To Int => 
    -r(Value A);
```

## Use

```
r: Some Record [5 to Some Record];
```

```
sum: Int [some list to half sum Int];
```

```
e: Some Enum [2 to Some Enum];
```

```
mapping: (Int => String) [(i) => i to String];
strings: {String*} [ints with mapping to {String*}];
```

```
strings: {String*} [ints with [(i) => i to String] to {String*}];
```
