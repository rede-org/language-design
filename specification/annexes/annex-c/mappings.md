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
Int per (Int => Int) to Some Record: (i, mapping) => 
    {Value A [i], Value B [i -> mapping]}.
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
{Int*} to half sum Int: (list) => list mapped to Int by [(i, sum) => sum + i] / 2.
```

```
{Int*} to doubled {Int*}: (list) => list mapped by [(i) => i * 2].
```

```
{Int*} with (Int => String) to {String*}: (list, mapping) => list mapped by mapping.
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

```
`Declare a simple record to track an index with a value.`
Iterable Value (T): 
    {
        index: Int,
        value: T
    },
    
    `Create an operator to easily create updated values.`
    Increment this and update with (T => T): (update mapping) =>
        {
            index [this(index) + 1],
            value [this(value) -> update mapping]
        }.


`Declare a mapping to condense a list to a record.
 The offset is used in the nested anonymous mapping, making a closure.`
{Int*} with Int to Some Record: (list, offset) => 
    list mapped to Iterable Value(Some Record) by
        [
            (i, v) ?? 
                v(index) < 10 => Increment v and update with 
                    [
                        (value) => value + {A[value(A) + i + offset]}
                    ],
                v(index) = 10 => Increment v and update with
                    [
                        (value) => value + {B[value(B) + i + offset]}
                    ],
                default => Increment v and update with 
                    [
                        (value) => value + {C[value(C) + i + offset]}
                    ]
        ] (value).  `Retrieve and finally return the value of the Iterable Value.`
```

```
`General generic mapping.`
(TValue) updated to (TValue): (v) => v * v;
```

```
`Contract-specific generic mapping.`
[Number] update to [Number]: (n) => n + n / 4;
```

#### With Identifiers

```
Get A :: Some Record to Int: (r) => r(Value A).

`Use within an Operation to declare a value from a Mapping result.`
i: Int [r -> Get A];
```

#### With Replacements

```
Some Record to Int: (r) replaces Get A => 
    -r(Value A).
```

## Use

```
r: Some Record [5];  `The "to Some Record", for the mapping, is implicit.`
```

```
sum: Int [some list to half sum Int];  `Type details after "to" must be explicit.`
```

```
e: Some Enum [2];  `The "to Some Enum", for the mapping, is implicit.`
```

```
mapping: (Int => String) [(i) => i to String];
s: String [2 -> mapping];
```

```
mapping: (Int, Int => Special Int) [(a, b) => a + b to Special Int];
s: Special Int [[2, 3] -> mapping];
```

```
mapping: (Int => String) [(i) => i to String];
strings: {String*} [ints with mapping];  `"to {String*}" is implicit.`
```

```
strings: {String*} [ints with [(i) => i to String]];  `"to {String*}" is implicit.`
```

```
`General generic anonymous mapping.`
mapping: ((T) => String) [(t) => "Mapped: \(t to String)"];
s: String [2 -> mapping];
```

```
`Contract-specific anonymous generic mapping.`
mapping: ([Number] => String) [(t) => "Mapped: \(t to String)"];
s: String [2 -> mapping];
```
