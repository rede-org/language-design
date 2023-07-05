---
description: >-
  The following code examples and sub-pages demonstrate the built-in value-based
  collection types offered by the language. See section [TBD] for details.
---

# Value Collections

## As Variables

### Assignment

```
some list is {1, 2, 2, 3},
```

```
some list is list a + list b,
```

### Declaration

```
some array: {Int**} [1, 2, 3];  `Undefined array size.`
```

```
some array: {Int*3*} [1, 2, 3];  `Allocate size of 3 elements.`
```

```
some array: {Int[-1]*10*} [1, 2, 3];  `Expect size 10, default to -1 if undefined.`
```

```
some list: {Int*} [1, 2, 3];
```

```
some specific list: List Name [1, 2, 3];
```

```
some list: {Int*} [list a + list b];
```

```
some dict: {String, Int[-1]} [some list];  `Unique values become keys, -1 values.`
```
