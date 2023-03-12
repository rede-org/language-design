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
some list: {Int*} [1, 2, 3];
some list (0?) = true    `The index 0 has a value in the list.`
some list (3?) = false  `The index 3 does not have a value in the list.`
```

```
some list: {Int*} [1, 2, 3];
some list (0?, 3?) = {true, false}  `Whether there is a value for each index.`
```

```
some list: {Int*} [1, 2, 3];
some list (0 ? -1) = 1  `Provide the value at index 0, or default to -1.`
some list (3 ? -1) = -1
```

```
some list: {Int*} [1, 2, 3];
some list (0 ? -1, 3 ? -1) = {1, -1}
```

```
some list: {Int*} [1, 2, 3];
some list ([1, 4)?) = {true, true, false}  `Check for indices in range [1, 4).`
```

```
some list: {Int*} [1, 2, 3];
some list ([1, 4) ? -1) = {2, 3, -1}
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
