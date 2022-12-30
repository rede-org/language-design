---
description: >-
  The following code examples demonstrate how lists can be declared and used.
  See section [TBD] for details.
---

# Lists

## Type Declaration

```
listName: {int*}.
```

## Accessing

### Containment

```
someList: {int*}, {1, 2, 3};
someList(0?) = true    `The index 0 has a value in the list.`
somneList(3?) = false  `The index 3 does not have a value in the list.`
```

```
someList: {int*}, {1, 2, 3};
someList(0?, 3?) = {true, false}  `Per whether the indices have values in the list.`
```

```
someList: {int*}, {1, 2, 3};
someList(0 ? -1) = 1
someList(3 ? -1) = -1
```

```
someList: {int*}, {1, 2, 3};
someList(0 ? -1, 3 ? -1) = {1, -1}
```

```
someList: {int*}, {1, 2, 3};
someList([1, 4)?) = {true, true, false}
```

```
someList: {int*}, {1, 2, 3};
someList([1, 4) ? -1) = {2, 3, -1}
```

### Retrieving

```
someList: {int*}, {1, 2, 3};
someList(0) = 1
```

```
someList: {int*}, {1, 2, 3};
someList(0, 2) = {1, 3}
```

```
someList: {int*}, {1, 2, 3};
someList(-1) = {3}
```

```
someList: {int*}, {1, 2, 3};
someList!(0) = {2, 3}
```

```
someList: {int*}, {1, 2, 3};
someList(...) = {1, 2, 3}  `Total collection accessor.`
```

```
someList: {int*}, {1, 2, 3};
someList((0, 2]) = {2, 3}
```

```
someList: {int*}, {1, 2, 3};
someList!((0, 2]) = {1}
```

### Setting

```
someList(0) is 1,
```

```
someList(0, 2) is {1, 3},
```

```
someList([1, 4]) = {1, 3, 4, 2},
```

## Operators

### Count

```
|someList| = 5
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

someList: {int*}, {1, 2, 2, 3};
```

#### Approximate

```
someSet: {int}, {1, 2, 3};
someList ~ someSet
```

```
someDict: {int: int, -1}, {1[1], 2[1], 3[0]};
someList ~ someDict
```

#### Collective

```
{1, 1} &= 1
{1, 2, 2, 1} &= {1, 2}
```

```
{true, true} &= true
{false, false} &= false
```

```
someList |= 1
someList |= {1, 3}
```

```
{true, false} |= true
{true, false} |= false
```

#### Strict

```
someList = {1, 2, 2, 3}
```

```
someList = {1, 2, ...}  `Match remaining values.`
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

## Variables

### Assignment

```
someList is {1, 2, 3},
```

```
someList is listA + listB,
```

### Declaration

```
someList: {int*}, {1, 2, 3};
```

```
someList: var, otherList;  `List type determined by initialization value.`
```

```
someList: listName, {1, 2, 3};
```

```
someList: {int*}, listA + listB;
```
