---
description: >-
  The following code examples demonstrate the built-in dictionary type offered
  by the language. See section [TBD] for details.
---

# Dictionaries

## Type Declaration

```
Dict Name: {String: Int[-1]}.
```

## Accessing

### Containment

```
some dict: {String: Int[-1]} ["A"[0], "B"[1], "C"];

some dict ("A"?) = true
some dict ("D"?) = false
```

```
some dict: {String: Int[-1]} ["A"[0], "B"[1], "C"];

some dict ("A"?, "D"?) = {true, false}
```

```
some dict: {String: Int[-1]} ["A"[0], "B"[1], "C"];

some dict ("A" ? -1) = 0
some dict ("D" ? -1) = -1
```

```
some dict: {String: Int[-1]} ["A"[0], "B"[1], "C"];

some dict("A" ? -1, "D" ? -1) = {0, -1}
```

```
some dict: {String: Int[0]} ["A"[1], "B"[2], "C"];
keys: {string}, {"A", "B", "C", "D"}

`Provide default for any key not found.`
some list: {Int*}, some dict (keys(...) ? -1);
some list = {1, 2, 0, -1}
```

```
some dict: {String: Int[-1]} ["A"[0], "B"[1], "C"];

some record: var, some dict(ValueA["A" ? -1], ValueD["D" ? -1]);
some record = {ValueA[1], ValueD[-1]}
```

### Retrieving

```
some dict: {String: Int[-1]} ["A"[0], "B"[1], "C"];
some dict ("C") = -1
```

```
some dict: {String: Int[-1]} ["A"[0], "B"[1], "C"];
some dict !("C") = {"A"[0], "B"[1]}
```

```
some dict: {String: Int[-1]} ["A"[0], "B"[1], "C"];
some dict ("A", "C") = {0, -1}
```

```
some dict: {String: Int[-1]} ["A"[0], "B"[1], "C"];
some dict (ValueA["A"], ValueB["C"]) = {ValueA[0], ValueB[-1]}
```

```
some dict: {String: Int[-1]} ["A"[0], "B"[1], "C"];
some dict (...) = {0, 1, -1}  // Total collection accessor.
```

### Setting

```
some dict ("A") is 1,
```

```
some dict ("A", "B") is {1, 3},
```

## Operators

### Count

```
|some dict| = 5
```

```
|{"A"[0], "B"[1], "C"}| = 3
```

### Difference (Remove Elements)

```
{"A"[0], "B"[1], "C"[2]} - {"A", "D"} = {"B"[1], "C"[2]}
```

```
{"A"[3], "B"[4], "C"[5]} - {"A"[0], "B"[1]} = {"C"[5]}
```

### Equality

#### Setup

```
`Assume the following for all equality code examples.`

some dict: {Int: Int[-1]} [1[1], 2[1], 3[0]];
```

#### Approximate

```
some list: {Int*} [1, 2, 2, 3];
some dict ~ some list
```

```
some set: {Int} [1, 2, 3];
some dict ~ some set
```

#### Strict

```
some dict = {1[1], 2[1], 3[0]}
```

```
some dict = {1[1], 2[1], ...}  `Match remaining keys and their values.`
```

### Intersection

```
{"A"[0], "B"[1], "C"[2]} % {"A", "D"} = {"A"[0]}
```

```
{"A"[3], "B"[4], "C"[5]} % {"A"[0], "B"[1]} = {"A"[3], "B"[4]}
```

```
{"A"[0], "B"[1], "C"[2]} % {"B", "A"} = {"A"[0], "B"[1]}
```

### Union (Appending)

```
`Default int value is assigned to "D" through the union.`
{"A"[0], "B"[1], "C"[2]} + {"A", "D"} = {"A"[0], "B"[1], "C"[2]. "D"[0]}
```

```
some dict: {String: Int[-1]} ["A"[0], "B"[1], "C"[2]];
some dict + {"A", "D"} = {"A"[0], "B"[1], "C"[2]. "D"[-1]}
```

```
{"A"[0], "B"[1]} + {"A"[1], "C"[1]} = {"A"[0], "B"[1], "C"[1]}
```

```
Dict Name: {String: Int[-1]}.
{"A", "C"} as Dict Name + {"A"[0], "B"[1]} = {"A"[-1], "B"[1], "C"[-1]}
```
