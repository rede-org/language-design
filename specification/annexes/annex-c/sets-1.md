---
description: >-
  The following code examples demonstrate how sets can be declared and used. See
  section [TBD] for details.
---

# Sets

## Type Declaration

```
setName: {int}.
```

## Accessing

### Containment

```
someSet: {int}, {1, 2, 3};
someSet(1?) = true
someSet(4?) = false
```

```
someSet: {int}, {1, 2, 3};
someSet(1?, 4?) = {true, false}
```

### Retrieving

```
someSet: {int}, {1, 2, 3};
someSet(...) = {1, 2, 3}  `Total collection accessor.`
```

## Operators

### Count

```
|{1, 2, 3} as {int}| = 3
```

```
|someSet| = 5
```

### Difference (Remove Elements)

<pre><code><strong>{1, 2, 3} as {int} - {2, 3, 4, 5} = {1}
</strong></code></pre>

```
{2, 3, 4, 5} as {int} - {1, 2, 3} = {4, 5}
```

### Equality

#### Setup

```
`Assume the following for all equality code examples.`

someSet: {int}, {1, 2, 3};
```

#### Approximate

```
someList: {int*}, {1, 2, 2, 3};
someSet ~ someList
```

```
someDict: {int: int, -1}, {1[1], 2[1], 3[0]};
someSet ~ someDict
```

#### Strict

```
someSet = {1, 2, 3}
```

```
someSet = {1, 2, ...}  `Match remaining values.`
```

### Intersection

```
{1, 2, 3} as {int} % {2, 3, 4, 5} = {2, 3}
```

```
{2, 3, 4, 5} as {int} % {1, 2, 3, 3} = {2, 3}
```

### Union (Appending)

```
{1, 2} as {int} + {2, 3} = {1, 2, 3}
```

```
{2, 3} as {int} + {1, 2} = {2, 3, 1}
```

## Variables

### Assignment

```
someSet is {1, 2, 3},
```

```
someSet is setA + setB,
```

### Declaration

```
someSet: {int}, {1, 2, 3};
```

```
someSet: var, otherSet;  `Set type determined by initialization value.`
```

```
someSet: setName, {1, 2, 3};
```

```
someSet: {int}, setA + setB;
```
