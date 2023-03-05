---
description: >-
  The following code examples demonstrate how namespaces, renames, and constants
  can be specified for parts of a codebase through the meta declaration. See
  section [TBD] for details.
---

# Meta

## General Declaration

```
Section Name: 
    in Some Namespace (Inner Namespace),
    using Other Namespace,
    New Name [Other Namespace (Other Name)].
```

## Assignment Variations

```
Section Name: in Some Namespace (Inner Namespace).
```

```
Section Name:  `Multiple namespace assignment, for three namespaces.`
    in Some Namespace (Inner Namespace, Other Inner Namespace),
    in Another Namespace( Inner Namespace (Inner Inner Namespace)).
```

## Reference Variations

```
Section Name: using OtherNamespace(InnerNamespace).
```

```
Section Name:  `Multiple namespace referencing, for three namespaces.`
    using Other Namespace (Inner Namespace, Other Inner Namespace),
    using Another Namespace (Inner Namspace (Inner Inner Namespace)).
```

## Renaming Variations

```
Section Name: New Context Name [Other Namespace (Other Context Name)].
```

```
Section Name: 
    New Context Name A [ Other Namespace (Other Context Name)],
    New Context Name B [Another Namespace (Inner Namespace (Another Context Name))].
```
