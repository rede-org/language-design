---
description: >-
  The following code examples demonstrate the built-in array type offered by the
  language. See section [TBD] for details.
---

# Arrays

## Type Declaration

```
Unsized Array Name: {Int**}.
```

```
Sized Array Name: {Int*10*}.
```

```
Sized Array Name: {Int[-1]*10*}.  `Array with 10 elements, with -1 as default value.`
```

## Accessing

### Containment

```
some array: {String**} ["b", "c", "d"];
some array ("a"?) = false  `The value "a" is not in the array.`
some array ("b"?) = true   `The value "b" is in the array.`
```

```
some array: {String**} ["b", "c", "d"];
some array ("a"?, "b"?) = {false, true}  `Whether each value is in the array.`
```

```
some array: {String**} ["b", "c", "d"];
some array (0 ? "a") = "b"  `Provide the value at index 0, or default to "a".`
some array (3 ? "a") = "a"
```

```
some array: {String**} ["b", "c", "d"];
some array (0 ? "a", 3 ? "a") = {"b", "a"}
```

```
some array: {String**} ["b", "c", "d"];
some array ({"a", "b"}?) = {false, true}  `Check for the values from the tuple.`
```

```
some array: {String**} ["b", "c", "d"];

`Provide the values in the range of indices [1, 3], or default to "a".`
r: Range [1, 3];
some array (r ? "a") = {"c", "d", "a"}
```

### Retrieving

```
some array: {Int**} [1, 2, 3];
some array (0) = 1
```

```
some array: {Int**} [1, 2, 3];
some array (0, 2) = {1, 3}
```

```
some array: {Int**} [1, 2, 3];
some array (-1) = {3}
```

```
some array: {Int**} [1, 2, 3];
some array !(0) = {2, 3}
```

```
some array: {Int**} [1, 2, 3];
some array (...) = {1, 2, 3}  `Total collection accessor.`
```

```
some array: {Int**} [1, 2, 3];
some array ((0, 2]) = {2, 3}
```

```
some array: {Int**} [1, 2, 3];
some array !((0, 2]) = {1}
```

### Setting

```
some array (0) is 1,
```

```
some array (0, 2) is {1, 3},
```

```
some array ([1, 4]) is {1, 3, 4, 2},
```

## Operators

### Count

```
|some array| = 5
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

some array: {Int**} [1, 2, 2, 3];
```

#### Approximate

```
some set: {Int} [1, 2, 3];
some array ~ some set
```

```
some dict: {Int: Int[-1]} [{1[1], 2[1], 3[0]}];
some array ~ some dict
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
some array |= 1  `At least one element matches the right-side element(s).`
some array |= {1, 3}
```

```
{true, false} |= true
{true, false} |= false
```

#### Strict

```
some array = {1, 2, 2, 3}
```

```
some array = {1, 2, ...}  `Match remaining values.`
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
