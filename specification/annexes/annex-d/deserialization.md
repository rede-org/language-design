---
description: >-
  The following program example demonstrates how contexts can be deserialized
  from a file upon program startup.
---

# Deserialization

## Set Up File

This code example requires built-in file loading functionality from the File IO namespace and built-in serialization functionality from the Serialization namespace. As such, the file housing all subsequent code is defined as using those namespaces through a [meta](../annex-c/meta.md) declaration.

```
Deserialization Example: 
    using File IO,
    using Serialization.
```

### Constructs Provided through the Usings

#### File To Read

This is a context alias for a string, essentially enabling a string to be identified differently to initiate a different set of operations than it might have otherwise. There is a mapping defined to convert this string to Formatted Serialized Text.

#### File Text

This is a [context](../annex-c/data-types/custom-types.md#context) representing the text read from or written to a file.

#### Formatted Serialized Text

This is a [context](../annex-c/data-types/custom-types.md#context) wrapping a [dictionary](../annex-c/data-types/built-in-types/value-collections/dictionaries.md) of strings mapped to their own Formatted Serialized Texts. This data structure provides an infinitely nestable format for serialized data.

## Example Code

```
`Declare the relevant contexts.`

Serialized Contexts: context Formatted Serialized Text.
```

```
`Declare an operation to perform the deserialization.`

Deserialize Serialized Contexts: <contexts>,
    foreach key in contexts,
    where type is key to Type?
        `Any type can be created through implicit casts 
            from Formatted Serialized Texts.`
        await !: type [contexts(key)]; as Registration.
    
    `The state of the application defined by the now-registered contexts will 
        continue the run of the application through behaviors.`
```

```
`Set up the program with a startup operation, and perform the deserialization.`

Main: when initialized?
    await <"serialized.data" as File To Read, file text: File Text;>,
    await <file text to Serialized Contexts>.
```
