---
description: >-
  The following program example demonstrates how contexts can be serialized to a
  file upon program startup.
---

# Serialization

## Set Up File

This code example requires built-in file loading functionality from the FileIO namespace and built-in serialization functionality from the Serialization namespace. As such, the file housing all subsequent code is defined as using those namespaces through a [meta](../annex-c/meta.md) declaration.

```
serializationExample: meta
    using FileIO,
    using Serialization.
```

### Constructs Provided through the Usings

#### FileToWrite

This is an [alias](../annex-c/aliasing.md) for a string, essentially enabling a string to be identified differently to initiate a different set of operations than it might have otherwise.

#### FileText

This is a [context](../annex-c/contexts.md) representing the text read from a file.

#### FormattedSerializedText

This is a [record](../annex-c/records.md) wrapping a [dictionary](../annex-c/dictionaries.md) of strings mapped to their own FormattedSerializedTexts. This data structure provides an infinitely nestable format for serialized data.

## Define Serialization Contexts

Contexts that encapsulate FormattedSerializedTexts are defined to enable the manipulation of such data through operations.

```
SerializedContext: context
	Context: FormattedSerializedText.

SerializedContexts: context
	Contexts: FormattedSerializedText.
```

## Define a Serializable Abstraction

There needs to be an abstraction of the serializable [contexts](../annex-c/contexts.md) to enable a behavior to indirectly reference them. This should be a context, but it doesn't need to have any actual data.

```
Serializable: context.
```

## Define Serializable Contexts

The [contexts](../annex-c/contexts.md) that should be serialized must also be defined. Through mutualism, these contexts can be represented by the previously defined Serializable abstraction.

```
ContextA: context
    Serializable: host Serializable;
    
    ValueA: int, -1;
    ValueB: string, "Test".

ContextB: context
    Serializable: host Serializable;
    
    ValueA: int, 0;
    ValueB: bool, false.
```

## Define Application State

The application may want to serialize and write the serializable contexts when it is in a specific save state. There needs to be a [context](../annex-c/contexts.md) to represent application state, to be able to track whether the application should save.

```
AppState: context
    ShouldSave: bool, false.
```

## Startup Operation

The operation that runs when the program initializes immediately creates/registers the application state (as the AppState [context](../annex-c/contexts.md)) and then it creates/registers the serializable contexts used in this example. For the purposes of this example, it then updates the AppState to be in a state where it should save.

```
main: operation when initialized?
    register appState: AppState;
    
    register ContextA;
    register ContextB;
    
    appState(ShouldSave) is true.
```

## Handling Saving (Serialization and Writing)

A behavior is defined to track the state of the application, as well as all serializable [contexts](../annex-c/contexts.md).

```
appSaveHandling: behavior<AppState appState, {*Serializable*} serializables>
```

This behavior defines an operation that occurs whenever the application is in a state where it should save. This operation initiates the serialization of the contexts and then initiates the writing of the serialized contexts to a file. Finally, it updates the application state to no longer be in a state in which it should save.

```
saveContexts: operation with appState,
    whenever appState(ShouldSave)?
    
    serialization: SerializedContexts;
    await serialization,
    
    await <"serialized.data" as FileToWrite, serialization(Contexts) to FileText>.
    appState(ShouldSave) is false;
```

This behavior also defines the operation that serializes the contexts. This operation is performed for each Serializable context known to the behavior, and for each context obtained from each Serializable through a mutualistic relationship. This is how the abstraction is reified as an actual serializable context, although the specific type of each context is not known to this operation. However, by initiating operations upon these contexts, the operations that are bound to the explicit typing of those contexts can occur and will be able to act upon such contexts with full knowledge of their typing.

For each such context, this operation attempts to initialize any operations that might define the FormattedSerializedText that encapsulates the serialization of the context. If no such operations are performed, then it defaults to the built-in cast of a context to a FormattedSerializedText. It then appends the resulting FormattedSerializedText to the complete serialization, the SerializedContexts.

```
serializeContexts: operation<SerializedContexts serialization> with serializables,
    foreach var serializable in serializables,
    foreach var context from serializable?
    
    serializedContext: SerializedContext;
    await <context, serializedContext> or 
        serializedContext(Context) is (context to FormattedSerializedText),
    
    serialization(Contexts) is serialization(Contexts) + serializedContext(Context).
```

## Custom Serialization

Lastly, a global operation to perform custom serialization for the defined ContextB is defined. This operation serves to override the default cast to a FormattedSerializedText, as is used in the previously defined behavior's operation. The functionality performed is simply to assign a custom string format of a ContextB to the in-progress FormattedSerializedText.

```
serializeContextB: operation<ContextB context, SerializedContext serializedContext>?
    serializedContext(Context) is "ContextB: {ValueA: " + context(ValueA) + "}".
```

This custom serialization could have been similarly achieved by defining a cast override for the ContextB context, as in the folllowing.

```
ContextB: context
    Serializable: host Serializable;
    
    ValueA: int, 0;
    ValueB: bool, false;
    
    this to FormattedSerializedText => 
    {
        "ContextB"[ValueA to FormattedSerialization]
    }.
```

