---
description: >-
  The following code examples demonstrate how an operation group can be declared
  and used. See section [TBD] for details.
---

# Groups

## General Declaration

```
`Operations can be grouped within an encapsulating operation, as a collection.
    Once the encapsulating operation qualifies, its inner operations will be 
    evaluated, and any of those that qualify will be performed. The contexts of 
    the encapsulating group are accessible to the inner operations.`

Op Group ID :: Some example operation group for Context A and Context B: 
    <context a, context b>?
    {
        Inner Operation A :: 
            when context a (Value A) > context b (Value A)?
                `Operation logic.`;
    
        Inner operation B ::
            when context a (Value B) > context b (Value B),
            after A, 
            with A?
                `Operation logic.`;
    
        Inner operation C ::
            after A,
            without B?
                `Operation logic.`;
    
        Inner operation D ::
            default?
                `Operation logic.`;
    }.

```

### Extensions

```
`Define a new operation to extend the operation group, Op Group ID, as 
    a new inner operation to be considered among the group's evaluation.`

E :: Inner operation E:
    extends Op Group ID,
    after B,
    with B?
        `Operation logic.`
```

### Replacements

```
`Define a new inner operation to replace an operation group's existing 
    inner operation, Op Group ID (B), whenever the new inner operation qualifies.`

B :: Inner operation B:
    replaces Op Group ID (B),
    when context a (Value C) < context b (Value C),
    after A,
    with A?
        `Operation logic.`
```
