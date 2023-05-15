---
description: >-
  The following code examples demonstrate the built-in list type offered by the
  language. See section [TBD] for details.
---

# Lists

## Type Declaration

```
List Name: {Int*}.
```

## Accessing

### Containment

```
some list: {Int*} ["b", "c", "d"];
some list ("a"?) = false  `The value "a" is not in the list.`
some list ("b"?) = true   `The value "b" is in the list.`
```

```
some list: {Int*} ["b", "c", "d"];
some list ("a"?, "b"?) = {false, true}  `Whether there is each value in the list.`
```

```
some list: {Int*} ["b", "c", "d"];
some list (0 ? "a") = "b"  `Provide the value at index 0, or default to "a".`
some list (3 ? "a") = "a"
```

```
some list: {Int*} ["b", "c", "d"];
some list (0 ? "a", 3 ? "a") = {"b", "a"}
```

```
some list: {Int*} ["b", "c", "d"];
some list ({"a", "b"}?) = {false, true}  `Check for the values from the tuple.`
```

```
some list: {Int*} ["b", "c", "d"];

`Provide the values in the range of indices [1, 4), or default to "a".`
some list ([1, 4) ? "a") = {"c", "d", "a"}
```

### Retrieving

```
some list: {Int*} [1, 2, 3];
some list (0) = 1
```

```
some list: {Int*} [1, 2, 3];
some list (0, 2) = {1, 3}
```

```
some list: {Int*} [1, 2, 3];
some list (-1) = {3}
```

```
some list: {Int*} [1, 2, 3];
some list !(0) = {2, 3}
```

```
some list: {Int*} [1, 2, 3];
some list (...) = {1, 2, 3}  `Total collection accessor.`
```

```
some list: {Int*} [1, 2, 3];
some list ((0, 2]) = {2, 3}
```

```
some list: {Int*} [1, 2, 3];
some list !((0, 2]) = {1}
```

### Setting

```
some list (0) is 1,
```

```
some list (0, 2) is {1, 3},
```

```
some list ([1, 4]) is {1, 3, 4, 2},
```

## Operators

### Count

```
|some list| = 5
```

```
|{1, 2, 3}| = 3
```

### Difference (Remove Elements)

```
{1, 2, 3, 3} - {2, 3, 4, 5} = {1, 3}
```

```
{2, 3, 4, 5} - {1, 2, 3, 3} = {4, 5}
```

### Equality

#### Setup

```
`Assume the following for all equality code examples.`

some list: {Int*} [1, 2, 2, 3];
```

#### Approximate

```
some set: {Int} [1, 2, 3];
some list ~ some set
```

```
some dict: {Int: Int[-1]} [{1[1], 2[1], 3[0]}];
some list ~ some dict
```

#### Collective

```
{1, 1} &= 1  `All elements match the right-side element(s).`
{1, 2, 2, 1} &= {1, 2}
```

```
{true, true} &= true
{false, false} &= false
```

```
some list |= 1  `At least one element matches the right-side element(s).`
some list |= {1, 3}
```

```
{true, false} |= true
{true, false} |= false
```

#### Strict

```
some list = {1, 2, 2, 3}
```

```
some list = {1, 2, ...}  `Match remaining values.`
```

### Intersection

```
{1, 2, 3, 3} % {2, 3, 4, 5} = {2, 3}
```

```
{2, 3, 4, 5} % {1, 2, 3, 3} = {2, 3}
```

```
{1, 2, 3, 3} % {3, 0, 1, 3} = {1, 3, 3}
```

### Union (Appending)

```
{1, 2} + {2, 3} = {1, 2, 2, 3}
```

```
{2, 3} + {1, 2} = {2, 3, 1, 2}
```
