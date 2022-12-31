---
description: >-
  The following code examples demonstrate how an enum type can be declared and
  used. See section [TBD] for details.
---

# Enums

## Type Declaration

```
enumName: [byte] A, B, C.
```

```
enumName: [int] A[100], B[101], C[102].
```

## Equality

```
enumName: [int] A[100], B[101], C[102].
enumName(A) = enumName(A)
```

```
enumName: [int] A[100], B[101], C[102].
enumName(A) = 100
```

```
enumName: [int] A[100], B[101], C[102].

e: enumName, A;
e = enumName(A)
```

```
enumName: [int] A[100], B[101], C[102].

e: enumName, A;
e = 100
```

## Variables

### Assignment

```
e is enumName(B),
```

### Declaration

```
e: enumName, A;
```
