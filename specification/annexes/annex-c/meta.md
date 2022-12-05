---
description: >-
  The following code examples demonstrate how namespaces, renames, and constants
  can be specified for parts of a codebase through the meta declaration. See
  section [TBD] for details.
---

# Meta

## Constants

```
sectionName: meta ConstantA: const int, -1; ConstantB: const bool, true.
```

```
sectionName: meta
    ConstantA: const int, -1;
    ConstantB: const bool, true.
```

## Namespacing

### Assignment

```
sectionName: meta in SomeNamespace(InnerNamespace).
```

```
sectionName: meta  `Multiple namespace assignment, for three namespaces.`
    in SomeNamespace(InnerNamespace, OtherInnerNamespace),
    in AnotherNamespace(InnerNamespace(InnerInnerNamespace)).
```

### Reference

```
sectionName: meta using OtherNamespace(InnerNamespace).
```

```
sectionName: meta  `Multiple namespace referencing, for three namespaces.`
    using OtherNamespace(InnerNamespace, OtherInnerNamespace),
    using AnotherNamespace(InnerNamspace(InnerInnerNamespace)).
```

## Renaming

```
sectionName: meta newContextName[OtherNamespace(otherContextName)].
```

```
sectionName: meta
    newContextNameA[OtherNamespace(otherContextName)],
    newContextNameB[AnotherNamespace(InnerNamespace(anotherContextName))].
```
