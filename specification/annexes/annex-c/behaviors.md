---
description: >-
  The following code examples demonstrate how a behavior can be declared and
  used. See section [TBD] for details.
---

# Behaviors

## General Declaration

```
Some example behavior for Context A and Context B: 
    {context a, context b}?
    
    Initialization operation: for {context a, context b},
        when initialized?
            `Operation logic.`
    
    Do some example operation: for {context a},
        whenever context a (Value A) changes?
            `Operation logic.`
    
    Do some other example operation for Context C: <context c> for {context b},
        when context c (Value A) = context b (Value A)?
            `Operaton logic.`
```

### Exclusivity

```
`Contexts are unique by default, being associated with only one behavior instance, 
    but this can be declared explicitly.`
    
Some example behavior for unique Context A and Context B: 
    {context a, context b}?
    
    `Declare Operations.`
```

```
`Shared contexts can be shared between behavior instances.`

Some example behavior for shared Context A and Context B: 
    {context a, context b}?
    
    `Declare Operations.`
```

### Fulfillment

```
`Contexts are expected to already exist by default, thus requiring all contexts 
    to be registered intentionally for a behavior instance to be created, but 
    this fulfillment can be declared explicitly.`
    
Some example behavior for existing Context A and Context B: 
    {context a, context b}?
    
    `Declare Operations.`
```

```
`Default contexts are created by the behavior with all default values once all 
    other context dependencies have been met.`

Some example behavior for default Context A and Context B: 
    {context a, context b}?
    
    `Declare Operations.`
```

```
`Optional contexts are created by the behavior with all default values once all 
    other context dependencies have been met, unless there is a matching context 
    explicitly associated (registered with) the behavior's other dependencies.`

Some example behavior for optional Context A and Context B: 
    {context a, context b}?
    
    `Declare Operations.`
```

### Specifier

```
`Contexts are expected to be independent by default, thus persisting regardless of 
    the existence of their associated behaviors, but this specifier can 
    be declared explicitly.`

Some example behavior for independent Context A and Context B: 
    {context a, context b}?
    
    `Declare Operations.`
```

```
`Coexistent contexts are automatically deregistered if the behavior 
    is destroyed (due to other dependencies being deregistered).`

Some example behavior for coexistent Context A and Context B: 
    {context a, context b}?
    
    `Declare Operations.`
```

### In Combination

```
Some example behavior for shared coexistent default Context A and Context B: 
    {context a, context b}?
    
    `Declare Operations.`
```

## Identification-Based Declarations

### With Identifier

```
Some Example Behavior :: Some example behavior for Context A and Context B:
    {context a, context b}?
    
    `Declare Operations.`
```

### Extensions

```
`Extension behaviors qualify based on their conditions and whether their extended 
    behavior has been qualified.`

Another example behavior for Context A, Context B, and Context C:
    {context a, context b, context c} extends Some Example Behavior 
        for {context a, context b}?
    
    `Declare extending Operations.`
```

### Replacements

```
`Replacement behaviors supercede their specified replaced behaviors.
    If a replacement behavior qualifies, the replaced behavior will be destroyed 
    and recreated as the replacement behavior.`

Another example behavior for Context A, Context B, and Context C:
    {context a, context b, context c} replaces Some Example Behavior?
    
    `Declare replacement Operations.`
```

## With Conditions

```
Some example behavior for Context A and Context B: {context a, context b}, 
    when context a (Value A) < context b (Value A)?
    
    `Declare Operations.`
```

## With Filtering

```
`Filter for a Behavior.`
`Generic 'T' is treated as the defined type, Base Context.`

Manage {*T*} (T [Base Context]): {contexts},
    where contexts filtered by [(a) => a meets criteria]?
    
    `Behavior Operations.`
```

## With Sorting

```
`Sort for a Behavior.`
`Generic 'T' is treated as the defined type, Base Context.`

Manage {*T*} (T [Base Context]): {contexts},
    where contexts sorted by [(a, b => a - b]?
    
    `Behavior Operations.`
```
