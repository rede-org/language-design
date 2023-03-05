---
description: >-
  The following code examples demonstrate the built-in set type offered by the
  language. See section [TBD] for details.
---

# Sets

## Declaration

```
Set Name: {*Int}.
```

## Accessing

### Containment

```
some set: {*Int} [1, 2, 3];
some set(1?) = true
some set(4?) = false
```

```
some set: {*Int} [1, 2, 3];
some set(1?, 4?) = {true, false}
```

### Retrieving

```
some set: {*Int} [1, 2, 3];
some set(...) = {1, 2, 3}  `Total collection accessor.`
```

## Operators

### Count

```
|{1, 2, 3} to {*Int}| = 3
```

```
|some set| = 5
```

### Difference (Remove Elements)

```
{1, 2, 3} to {*Int} - {2, 3, 4, 5} = {1}
```

```
{2, 3, 4, 5} to {*Int} - {1, 2, 3} = {4, 5}
```

### Equality

#### Setup

```
`Assume the following for all equality code examples.`

some set: {*Int} [1, 2, 3];
```

#### Approximate

```
some list: {Int*} [1, 2, 2, 3];
some set ~ some list
```

```
some dict: {Int: Int[-1]} [1[1], 2[1], 3[0]];
some set ~ some dict
```

#### Strict

```
some set = {1, 2, 3}
```

```
some set = {1, 2, ...}  `Match remaining values.`
```

### Intersection

```
{1, 2, 3} to {*Int} % {2, 3, 4, 5} = {2, 3}
```

```
{2, 3, 4, 5} to {*Int} % {1, 2, 3, 3} = {2, 3}
```

### Union (Appending)

```
{1, 2} to {*Int} + {2, 3} = {1, 2, 3}
```

```
{2, 3} to {*Int} + {1, 2} = {2, 3, 1}
```
