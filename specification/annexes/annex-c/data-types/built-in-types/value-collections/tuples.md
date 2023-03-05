---
description: >-
  The following code examples demonstrate the built-in tuple type offered by the
  language. See section [TBD] for details.
---

# Tuples

## Declaration

```
Tuple Name: {Int, Int, Bool}.
```

## Accessing

### Retrieving

```
some tuple: {Int, Int, Bool} [1, 2, false];
some tuple (0) = 1
```

```
some tuple: {Int, Int, Bool} [1, 2, false];
some tuple (0, 2) = {1, false}
```

```
some tuple: {Int, Int, Bool} [1, 2, false];
some tuple (-1) = {false}
```

```
some tuple: {Int, Int, Bool} [1, 2, false];
some tuple !(0) = {2, false}
```

```
some tuple: {Int, Int, Bool} [1, 2, false];
some tuple (...) = {1, 2, 3}  `Total collection accessor.`
```

```
some tuple: {Int, Int, Bool} [1, 2, false];
some tuple ((0, 2]) = {2, false}
```

```
some tuple: {Int, Int, Bool} [1, 2, false];
some tuple !((0, 2]) = {1}
```

### Setting

```
some tuple (0) is 1,
```

```
some tuple (0, 2) is {1, true},
```

```
some tuple ([0, 2]) is {1, 3, true}, `Range must be within the Tuple's bounds.`
```

## Operators

### Count

```
|{1, 2, false}| = 3
```

```
|some tuple| = 5
```

### Difference (by Type Matching)

```
{1, 2, false} - {3, true} = {2}
```

```
{2, 3, 4, 5} - {1, 2} = {4, 5}
```

### Equality

#### Setup

```
`Assume the following for all equality code examples.`

some tuple: {Int, Int, Bool} [1, 2, false];
```

#### Approximate

```
other tuple: {Bool, Int, Int} [false, 1, 2];
some tuple ~ other tuple
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
someTuple |= 1  `At least one element matches the right-side element(s).`
someTuple |= {1, true}
```

```
{true, false, 0} |= true
{true, 1, false} |= false
```

#### Strict

```
some tuple = {1, 2, false}
```

```
some tuple = {1, 2, ...}  `Match remaining values.`
```

### Intersection (by Type Matching)

```
{1, 2, false} % {2, 3, 4, 5} = {1, 2}
```

```
{2, 3, 4, 5} % {1, 2, 3, 3} = {2, 3, 4, 5}
```

### Union

```
{1, 2} + {2, false, 3} = {1, 2, 2, false, 3}
```

```
{2, 3} + {1, 2, true} = {2, 3, 1, 2, true}
```
