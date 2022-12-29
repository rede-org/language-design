---
description: >-
  The following code examples demonstrate how dictionaries can be declared and
  used. See section [TBD] for details.
---

# Dictionaries

## Type Declaration

```
dictName: {string: int, -1}.
```

## Accessing

### Containment

```
someDict: {string: int, -1}, {"A"[0], "B"[1], "C"};
someDict("A"?) = true
someDict("D"?) = false
```

```
someDict: {string: int, -1}, {"A"[0], "B"[1], "C"};
someDict("A"?, "D"?) = {true, false}
```

```
someDict: {string: int, -1}, {"A"[0], "B"[1], "C"};
someDict("A" ? -1) = 0
someDict("D" ? -1) = -1
```

```
someDict: {string: int, -1}, {"A"[0], "B"[1], "C"};
someDict("A" ? -1, "D" ? -1) = {0, -1}
```

### Retrieving

```
someDict: {string: int, -1}, {"A"[0], "B"[1], "C"};
someDict("C") = -1
```

```
someDict: {string: int, -1}, {"A"[0], "B"[1], "C"};
someDict("A", "C") = {0, -1}
```

```
someDict: {string: int, -1}, {"A"[0], "B"[1], "C"};
someDict(ValueA["A"], ValueB["C"]) = {ValueA[0], ValueB[-1]}
```

```
someDict: {string: int, -1}, {"A"[0], "B"[1], "C"};
someDict(...) = {0, 1, -1}  // Total collection accessor.
```

### Setting

```
someList("A") is 1,
```

```
someList("A", "B") is {1, 3},
```

## Operators

### Count

```
|someDict| = 5
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
// Some code
```

#### Approximate

```
// Some code
```

#### Collective

```
// Some code
```

#### Strict

```
// Some code
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

<pre><code><strong>`Default int value is assigned to "D" through the union.`
</strong><strong>{"A"[0], "B"[1], "C"[2]} + {"A", "D"} = {"A"[0], "B"[1], "C"[2]. "D"[0]}
</strong></code></pre>

```
someDict: {string: int, -1}, {"A"[0], "B"[1], "C"[2]};
someDict + {"A", "D"} = {"A"[0], "B"[1], "C"[2]. "D"[-1]}
```

```
{"A"[0], "B"[1]} + {"A"[1], "C"[1]} = {"A"[0], "B"[1], "C"[1]}
```

```
dictName: {string: int, -1}.
{"A", "C"} as dictName + {"A"[0], "B"[1]} = {"A"[-1], "B"[1], "C"[-1]}
```

## Variables

### Assignment

```
someDict is {"A"[0], "B"[1], "C"[2]},
```

```
someDict is dictA + dictB,
```

### Declaration

```
someDict: {string: int, -1}, {"A"[0], "B"[1], "C"[2]};
```

```
someDict: var, otherDict;  `Dictionary type determined by initialization value.`
```

```
someDict: dictName, {"A"[0], "B"[1], "C"[2]};
```

```
someDict: {string: int, -1}, dictA + dictB;
```
