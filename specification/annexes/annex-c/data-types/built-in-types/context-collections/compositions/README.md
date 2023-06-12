---
description: >-
  The following code examples demonstrate the built-in composition type offered
  by the language. See section [TBD] for details.
---

# Compositions

## Type Declaration

```
Specific Composition Name: Composition.
```

```
`Declare a composition that can only contain up to the specified types.`

Constrained Composition Name A: {Context A, Context B}.
Constrained Composition Name B: {Context A, Context B, Context B}.
Constrained Composition Name C: {Context A, {*Context B*}}.
```

## Operators

### Accessing

#### Containment

```
some composition: Composition [context a, context b];

`Index checks.`
some composition(1?) = true
some composition(2?) = false

`ID checks.`
some composition(context a id?) = true
some composition(context c id?) = false
```

```
some composition: Composition [context a, context b];
some composition(1?, context c id?) = {true, false}
```

#### Retrieving

```
some composition: Composition [context a, context b];
some composition(0) = {context a}
some composition(context b id) = {context b}
```

```
some composition: Composition [context a, context b];
some composition(...) = {context a, context b}  `Total collection accessor.`
```

### Await

```
`Await all reactive evaluations of the composition.`
await some composition,
```

```
`Await all reactive evaluations of the composition.`
await {some context, some other context, some bucket},
```

```
`Await any qualifying operation belonging to the composition.`
await some operable for some composition,
```

```
`Await any qualifying operation belonging to the composition.`
await <some context> for {other context},
```

```
`Await any qualifying operation belonging to the composition, and if none 
 are performed, await a different set of qualifying operations.`
await some operable for some composition or other operable for some composition,
```

```
`Await any qualifying operation belonging to the composition, and if at least one 
 is performed, await a different set of qualifying operations.`
await some operable for some composition and other operable for some composition,
```

### Difference (Remove Elements)

```
{context a, context b} - {context b, context c} = {context a}
```

### Expansion

```
`First Context B instance related to context a through a Behavior is unioned.`
{context a} # Context B = {context a, context b}
```

```
`All Context B instances related to context a through its Behaviors are unioned.`
{context a} # {*Context B*} = {context a, context b bucket}
```

### Intersection

```
{context a, context b} % {context b, context c} = {context b}
```

### Reduction

```
`All Context B instances are removed.`
{context a, context b, other context b} !# Context B = {context a}
```

```
`All Context B buckets are removed.`
{context a, context b bucket, context b} !# {*Context B*} = {context a, context b}
```

### Run

```
`Run all reactive evaluations of the composition.`
run some composition,
```

```
`Run all reactive evaluations of the composition.`
run {some context, some other context},
```

```
`Run any qualifying operation belonging to the composition.`
run some operable for some composition,
```

```
`Run any qualifying operation belonging to the composition.`
run <some context> for {other context},
```

```
`Run any qualifying operation belonging to the composition, and if none 
 are performed, run a different set of qualifying operations.`
run some operable for some composition or other operable for some composition,
```

```
`Run any qualifying operation belonging to the composition, and if at least one 
 is performed, run a different set of qualifying operations.`
run some operable for some composition and other operable for some composition,
```

### Union (Appending)

```
{context a, context b} + {context b, context c} = {context a, context b, context c}
```

```
{context a} + {{context a, context b}} = {context a, {context a, context c}}
```

## As Variables

### Assignment

```
some composition is {context a, context b},
```

```
some composition is {context a, context b} + {context b, context c},
```

```
some nested composition is {context a, {context b, context c}},
```

```
some composition is {context a} # Context B,
```

### Declaration

```
some composition: Composition [context a, context b];
```

```
specific composition: Specific Composition Name [context a, context b];
```

```
constrained composition: Constrained Composition Name A [context a];
```

```
constrained composition: Constrained Composition Name A [context a, context b];
```

```
some composition: Composition [{context a, context b} + {context b, context c}];
```

```
some composition: Composition [{context a} # Context B];
```

```
some nested composition: Composition [context a, some composition];
```
