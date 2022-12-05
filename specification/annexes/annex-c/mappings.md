# Mappings

The following code examples demonstrate how a mapping can be declared and used. See section \[TBD] for details.

## Declaration

### Context to Context

```
someMapping: contextName from otherContextName where
{
    ContextValueA = (OtherValueA(SubValue)),
    ContextValueB = (OtherValueB) + 1,
    ContextValueC = (OtherValueC)
}.
```

### Context to Record

```
someMapping: contextName from recordName where
{
    ContextValueA = (RecordValueA) to string,
    ContextValueB = (RecordValueB) + 1,
    ContextValueC = (RecordValueC)
}.
```

### Enum to Enum

```
someMapping: enumName from otherEnumName where
{
    A = (X),
    B = (Y), 
    C = (Z)
}.
```

### Record to Context

```
someMapping: recordName from contextName where
{
    RecordValueA = (ContextValueA) to int,
    RecordValueB = (ContextValueB) - 1,
    RecordValueC = (ContextValueC)
}.
```

### Record to Record

```
someMapping: recordName from otherRecordName where
{
    RecordValueA = (OtherValueA),
    RecordValueB = (OtherValueB) - 1,
    RecordValueC = (OtherValueC(SubValue)) to float
}.
```

### To Value Type

```
someNameToString: string from someName where value = "Debug: " + (ValueA).
```

```
someNameToInt: int from someName where value = (ValueA) + (ValueB) + (ValueC).
```

```
listToHalfSum: int from {int*} where 
{
    value += (...),
    value /= 2
}.
```

## Use

### Declared

```
someRecord: recordName, otherRecord with someMapping;
```

```
newContext: contextName, someRecord with someMapping;
```

```
someEnum = anEnum with someMapping,
```

```
someInt = someList with listToHalfSum,
```

### Inline

```
someRecord: recordName, otherRecord where
{
    RecordValueA = (OtherValueA),
    RecordValueB = (OtherValueB) - 1,
    RecordValueC = (OtherValueC(SubValue)) to float
}.
```

```
newContext: contextName, someRecord where
{
    ContextValueA = (RecordValueA) to string,
    ContextValueB = (RecordValueB) + 1,
    ContextValueC = (RecordValueC)
}.
```

```
someEnum = otherEnum where
{
    A = (X),
    B = (Y), 
    C = (Z)
},
```

```
someInt = someList where 
{
    value += (...),
    value /= 2
},
```
