---
description: >-
  The following code examples demonstrate how a mapping can be declared and
  used. See section [TBD] for details.
---

# Mappings

## Declaration

### Context to Context

```
someMapping: contextName from otherContextName where
{
    ContextValueA is (OtherValueA(SubValue)),
    ContextValueB is (OtherValueB) + 1,
    ContextValueC is (OtherValueC)
}.
```

### Context to Record

```
someMapping: contextName from recordName where
{
    ContextValueA is (RecordValueA) to string,
    ContextValueB is (RecordValueB) + 1,
    ContextValueC is (RecordValueC)
}.
```

### Enum to Enum

```
someMapping: enumName from otherEnumName where
{
    A is (X),
    B is (Y), 
    C is (Z)
}.
```

### Record to Context

```
someMapping: recordName from contextName where
{
    RecordValueA is (ContextValueA) to int,
    RecordValueB is (ContextValueB) - 1,
    RecordValueC is (ContextValueC)
}.
```

### Record to Record

```
someMapping: recordName from otherRecordName where
{
    RecordValueA is (OtherValueA),
    RecordValueB is (OtherValueB) - 1,
    RecordValueC is (OtherValueC(SubValue)) to float
}.
```

### To Value Type

```
someNameToString: string from someName where value is "Debug: " + (ValueA).
```

```
someNameToInt: int from someName where value is (ValueA) + (ValueB) + (ValueC).
```

```
listToHalfSum: int from {int*} where 
{
    value is value + (...),
    value is value / 2
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
someEnum is anEnum with someMapping,
```

```
someInt is someList with listToHalfSum,
```

### Inline

```
someRecord: recordName, otherRecord where
{
    RecordValueA is (OtherValueA),
    RecordValueB is (OtherValueB) - 1,
    RecordValueC is (OtherValueC(SubValue)) to float
}.
```

```
newContext: contextName, someRecord where
{
    ContextValueA is (RecordValueA) to string,
    ContextValueB is (RecordValueB) + 1,
    ContextValueC is (RecordValueC)
}.
```

```
someEnum is otherEnum where
{
    A is (X),
    B is (Y), 
    C is (Z)
},
```

```
someInt is someList where 
{
    value is value + (...),
    value is value / 2
},
```
