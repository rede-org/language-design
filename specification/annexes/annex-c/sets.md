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
someSet: setName, {1, 2, 3};
```

```
someSet: {int}, setA + setB;
```
