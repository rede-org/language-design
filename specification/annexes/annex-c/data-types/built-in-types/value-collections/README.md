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
some list: {int*} [1, 2, 3];
```

```
some list: listName [1, 2, 3];
```

```
some list: {int*} [listA + listB];
```

```
some dict: {string, int[-1]} [someList];  `Unique values become keys, -1 values.`
```
