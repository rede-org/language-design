---
description: >-
  The following code examples demonstrate how a record type can be declared and
  used. See section [TBD] for details.
---

# Records

## Type Declaration

```
recordName: 
{
    SomeConstant: const int, 2;
    ValueA: recordName, {A[1], B[""]};
    ValueB: readonly float, 1.5;
    ValueC: {float*}, {1.0, 0.5, 1.0};
    ValueD: {A: int, -1; B: int;}, {B[2]};
}.
```

### Generic

```
recordName(TValue):
{
    ValueA: TValue;
    ValueB: otherGenericRecordName(TValue);
}.
```

### With In-lined Value Aliasing

```
recordName:
{
    ValueA: recordName;
    ValueAliasA[ValueA(A)],
    ValueAliasB[ValueB(B)]
}.
```

## Accessing

### Retrieving

```
someRecord: {ValueA: int, -1; ValueB: int;}, {ValueB[2]};
someRecord(ValueA) = -1
```

```
someRecord: {ValueA: int, -1; ValueB: int;}, {ValueB[2]};
someRecord(ValueA, ValueB) = {-1, 2}
```

```
someRecord: {ValueA: int, -1; ValueB: int;}, {ValueB[2]};
someRecord(...) = {-1, 2}
```

```
someRecord: {ValueA: int, -1; ValueB: int;}, {ValueB[2]};
someRecord!(ValueA) = 2
```

### Setting

```
someRecord(ValueA) is 2,
```

```
someRecord(ValueA, ValueB) is {ValueA[1], ValueB[""]},
```

```
someRecord(ValueA, ValueB) is otherRecord(ValueA, ValueB),
```

```
someRecord(ValueA, ValueB) is otherRecord(ValueA[ValueC], ValueB[ValueD]),
```

```
someRecord!(ValueA, ValueB) is {ValueC[3.5], ValueD[0], ValueE[true]},
```

```
someRecord!(ValueA, ValueB) is {ValueC[3.5], ...},  `Match remaining values.`
```

```
someRecord(...) is matchingRecord,  `Assign all values.`
```

```
someRecord(...) is otherRecord with recordMapping,
```

```
someRecord(...) is otherRecord where
{
    ValueA is RecordValueA,
    ValueB is RecordValueB
},
```

```
someRecord(...) is {ValueA[1], ValueB[""], ...},  `Match remaining values.`
```

## Operators

### Difference

```
someRecord: {ValueA: int, -1; ValueB: int;}, {ValueB[2]};
otherRecord: {ValueA: int, 0;}, { };

someRecord - otherRecord = {ValueB[2]}
```

```
recordName:
{
    ValueA: int, 0;
    ValueC: int -1;
}.

someRecord: {ValueA: int, -1; ValueB: int;}, {ValueB[2]};

someRecord - recordName = {ValueB[2]}
```

### Equality

#### Setup

```
`Assume the following for all equality code examples.`

contextName: context
    ValueA: int, -1;
    ValueB: string, "".

recordName:
{
    ValueA: int, -1;
    ValueB: string, "";
}.

c: contextName;
r: recordName;
```

#### Approximate

```
r ~ {ValueA[-1]},
```

```
r(ValueA, ValueB) ~ c(ValueB),
```

#### Strict

```
r = c,
```

```
r = {ValueA[-1], ValueB[""]},
```

```
r = {ValueA[-1], ...},  `Match remaining values.`
```

```
r(ValueA, ValueB) = {ValueA[-1], ValueB[""]},
```

```
r(ValueA, ValueB) = c(ValueA, ValueB),
```

### Intersection

```
someRecord: {ValueA: int, -1; ValueB: int;}, {ValueB[2]};
otherRecord: {ValueA: int, 0;}, { };

someRecord % otherRecord = {ValueA[-1]}
```

```
recordName:
{
    ValueA: int, 0;
    ValueC: int -1;
}.

someRecord: {ValueA: int, -1; ValueB: int;}, {ValueB[2]};

someRecord % recordName = {ValueA[-1]}
```

### Union

```
someRecord: {ValueA: int, -1; ValueB: int;}, {ValueB[2]};
otherRecord: {ValueA: int, 0; ValueC: int, 0;}, { };

someRecord + otherRecord = {ValueA[-1], ValueB[2], ValueC[0]}
```

```
recordName:
{
    ValueA: int, 0;
    ValueC: int -1;
}.

someRecord: {ValueA: int, -1; ValueB: int;}, {ValueB[2]};

someRecord + recordName = {ValueA[-1], ValueB[2], ValueC[-1]}
```

## Variables

### Assignment

```
someRecord is {ValueA[1], ValueB[""]},
```

```
someRecord is {ValueA[1], ...},  `Match (default)remaining values.`
```

### Declaration

```
someRecord: recordName;  `Declare with all default values.`
```

```
someRecord: genericRecordName(int); `Declare with all default values.`
```

```
someRecord: {ValueA: int, -1; ValueB: int;}, {ValueB[2]};  `Anonymous record.`
```

```
someRecord: recordName, {ValueA[1], ValueB[""]};  `Default unspecified values.`
```

```
someRecord: genericRecordName(int), {GenericValueA[1], NonGenericValueA[""]};
```

```
someRecord: recordName, matchingRecord;
```

```
someRecord: recordName, matchingContext;
```

```
`Anonymous record composed of two unioned record types.
 Initialized values specified by unioned record instances.`
someRecord: recordNameA + recordNameB, recordA + recordB;
```

```
`Anonymous record defined by the initialization value.`
someRecord: var, recordA + {ValueC[1]};
```

```
someRecord: recordName, someRecord with recordMapping;
```

```
someRecord: recordName, someRecord where
{
    ValueA is RecordValueA,
    ValueB is RecordValueB
};
```
