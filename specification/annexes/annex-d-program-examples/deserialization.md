---
description: >-
  The following program example demonstrates how contexts can be deserialized
  from a file upon program startup.
---

# Deserialization

## Set Up File

This code example requires built-in file loading functionality from the FileIO namespace and built-in serialization functionality from the Serialization namespace. As such, the file housing all subsequent code is defined as using those namespaces through a [meta](../annex-c/meta.md) declaration.

```
deserializationExample: meta
    using FileIO,
    using Serialization.
```

### Constructs Provided through the Usings

#### FileToRead

This is an [alias](../annex-c/aliasing.md) for a string, essentially enabling a string to be identified differently to initiate a different set of operations than it might have otherwise.

#### FileText

This is a [context](../annex-c/contexts.md) representing the text read from a file.

#### FormattedSerializedText

This is a [context](../annex-c/contexts.md) wrapping a [dictionary](../annex-c/dictionaries.md) of strings mapped to their own FormattedSerializedTexts. This data structure provides an infinitely nestable format for serialized data.

## Define Aliases

An [alias](../annex-c/aliasing.md) is defined for FormattedSerializedText, so that the expected operations to be performed to FormattedSerializedText in this specific situation can better defined.

```
UnprocessedSerializedContexts: [FormattedSerializedText] ...
```

## Startup Operation

The operation that runs when the program initializes immediately expects operations to read text from a file, putting the read text in the provided FileText. It then converts that text to the built-in FormattedSerializedText context. The operation then initiates subsequent operations to process that context under the UnprocessedSerializedContexts alias.

```
main: operation when initialized?
    fileText: FileText;
    await <"serialized.data" as FileToRead, fileText>,
    
    serializedText: var, fileText to FormattedSerializedText;
    await <serializedText as UnprocessedSerializedContexts>.
```

## Deserialization Operation

This operation picks up where the startup operation left off by processing the UnprocessedSerializedContexts. It does so by operating on each serialized type (each key) of the provided serialized contexts, so long as the data associated with the key has content; that the size of the nested FormattedSerializedText is not zero.

For qualifying types, a context of the type identified by the string is created with data defined by the FormattedSerializedTexts associated with that type. As with anonymous records, FormattedSerializedTexts or any variation of a dictionary with string keys can be implicitly cast to an instance of a context or record.

Finally, the newly declared context is registered. This enables any behaviors dependent on such contexts to initialize and begin their operations, effectively defining the state and current functionality of the application from the loaded data.

```
processSerializedContexts: operation<UnprocessedSerializedContexts contexts>
    foreach string type in contexts,
    when |contexts(type)| > 0?
    
    deserializedContext: type, contexts(type);
    register deserializedContext.
```
