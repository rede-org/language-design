---
description: >-
  The following code examples demonstrate how dictionaries can be declared and
  used. See section [TBD] for details.
---

# Dictionaries

## Variables

### Assignment

```
someDict is {"A"[0], "B"[1], "C"[2]},
```

```
someDict is dictA + dictB,
```

### Declaration

```
someDict: {string: int, -1}, {"A"[0], "B"[1], "C"[2]};
```

```
someDict: var, otherDict;  `Dictionary type determined by initialization value.`
```

```
someDict: dictName, {"A"[0], "B"[1], "C"[2]};
```

```
someDict: {string: int, -1}, dictA + dictB;
```

```
someDict: {string, int, -1}, someList;  `Unique list values become keys, -1 values.`
```
