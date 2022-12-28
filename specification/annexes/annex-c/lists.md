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
// Some code
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
someList(...) = {1, 2, 3}  // Total collection accessor.
```

### Setting

```
someList(0) is 1,
```

```
someList(0, 2) is {1, 3},
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
// Some code
```

#### Approximate

```
// Some code
```

#### Strict

```
// Some code
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
