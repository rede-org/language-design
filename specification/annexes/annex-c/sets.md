---
description: >-
  The following code examples demonstrate how sets can be declared and used. See
  section [TBD] for details.
---

# Sets

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
someSet: {*int}, {1, 2, 3};
```

```
someSet: var, otherSet;  `Set type determined by initialization value.`
```

```
someSet: setName, {1, 2, 3};
```

```
someSet: {*int}, setA + setB;
```
