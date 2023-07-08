---
description: >-
  The following program example demonstrates how contexts can be serialized to a
  file upon program startup.
---

# Serialization

## Set Up File

This code example requires built-in file loading functionality from the FileIO namespace and built-in serialization functionality from the Serialization namespace. As such, the file housing all subsequent code is defined as using those namespaces through a [meta](../annex-c/meta.md) declaration.

```
Serialization Example: meta
    using FileIO,
    using Serialization.
```

### Constructs Provided through the Usings

#### File To Write

This is an alias for a string, essentially enabling a string to be identified differently to initiate a different set of operations than it might have otherwise.

#### File Text

This is a [context](../annex-c/data-types/custom-types.md#context) representing the text read from or written to a file.

#### Formatted Serialized Text

This is a [context](../annex-c/data-types/custom-types.md#context) wrapping a [dictionary](../annex-c/data-types/built-in-types/value-collections/dictionaries.md) of strings mapped to their own Formatted Serialized Texts. This data structure provides an infinitely nestable format for serialized data.

## Example Code

```
`Declare the relevant contexts.`

Serialized Context: context Formatted Serialized Text.
Serialized Contexts: context Formatted Serialized Text.
Serializable: contract.

App State: context
    {
        Should Save: bool [false];
    }.
Context A [Serializable]: context
    {
        ValueA: int [-1];
        ValueB: string ["Test"];
    }.
Context B [Serializable]: context
    {
        ValueA: int [0];
        ValueB: bool [false];
    }.
```

```
`Declare the behavior to perform the serialization.`

Manage {*Serializable*} according to App State: {serializables, state}?
    Write serializables on save:
        for {state}, whenever state(Should Save)?
            await serialization: Serialized Contexts;
            await <"serialized.data" as File To Write, serialization to File Text>.

            state(Should Save) is false;

Serialize contexts to Serialized Contexts: <serialization> for {serializables},
    foreach serializable in serializables?
        serialized context: Serialized Context;

        `Build the serialized context from a custom serialization operation, 
            or use the default mapping.`
        await <serializable, serialized context> or 
        serialized context is serializable to Formatted Serialized Text,

        serialization is serialization + serializedContext.
```

```
`Declare a custom serialization operation for Context B.`

Serialize Context B to Serialized Context: <context, serialized context>?
    serialized context is "ContextB: {ValueA: " + context(ValueA) + "}".
```

```
`Set up the program with a startup operation, and perform the serialization.`

Main: when initialized?
    await app state: AppState; as Registration,
    await !: Context A; as Registration,
    await !: Context B; as Registration,

    app State(Should Save) is true.
```

