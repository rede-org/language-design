---
description: >-
  The following code examples demonstrate how data evaluations can be triggered
  within the language. See section [TBD] for details.
---

# Evaluation

## Control Flow

All control flow is accomplished through synchronous or asynchronous performance of operations, which define their own internal control flow. Refer to matching data type documentation for details on each type of data being manipulated.

### Asynchronous

```
`Initiate non-behavior operations depending on the context.`
run some context,
```

```
`Initiate non-behavior operations depending on the bucket.`
run some bucket,
```

```
`Initiate non-behavior operations matching the operable.`
run <some context, some bucket>,
```

```
`Initiate non-behavior operations for the undeclared context.`
run !: Context Name [A[1], B[""]];
```

```
`Initiate non-behavior operations matching the operable.`
run some operable,
```

```
`Initiate all operations matching the operable for the behaviors 
    that match the composition.`
run some operable for some composition,
```

```
`Conditionally initiate operations matching the second operable if there were 
    no operations that started for the first operable.`
run some operable or another operable,
```

```
`Conditionally initiate operations matching the second operable if there was 
    at least one operation that started for the first operable.`
run some operable and another operable.
```

```
`Initiate all currently scheduled reactive operations of the composition.`
run some composition,
```

### Synchronous

```
`Wait on all non-behavior operations depending on the context.`
await some context,
```

```
`Wait on all non-behavior operations depending on the bucket.`
await some bucket,
```

```
`Wait on non-behavior operations matching the operable.`
await <some context, some bucket>,
```

```
`Wait on non-behavior operations for the undeclared context.`
await !: Context Name [A[1], B[""]];
```

```
`Wait on non-behavior operations matching the operable.`
await some operable,
```

```
`Wait on all operations matching the operable for the behaviors 
    that match the composition.`
await some operable for some composition,
```

```
`Conditionally wait on operations matching the second operable if there were 
    no operations that completed for the first operable.`
await some operable or another operable,
```

```
`Conditionally wait on operations matching the second operable if there was 
    at least one operation that completed for the first operable.`
await some operable and another operable.
```

```
`Wait for all currently scheduled reactive operations of the composition complete.`
await some composition,
```

```
`Wait for all currently scheduled reactive operations across the 
    application to complete.`
continue,
```

## Registration Management

### Asynchronous

```
await some context as Registration,
```

```
await some context as Deregistration,
```

```
some registration: Registration [some composition];
await some registration,
```

```
await some registration as Deregistration,
```

```
await {context A, context B} as Deregistration,
```

```
await !: Context Name [A[1], B[""]]; as Registration,
```

```
await some context: Context Name [A[1], B[""]]; as Registration,
```

### Synchronous

```
run some context as Registration,
```

```
run some context as Deregistration,
```

```
some registration: Registration [some composition];
run some registration,
```

```
run some registration as Deregistration,
```

```
run {context A, context B} as Deregistration,
```

```
run !: Context Name [A[1], B[""]]; as Registration,
```

```
run some context: Context Name [A[1], B[""]]; as Registration,
```
