---
description: >-
  The following code examples demonstrate how a context type can be declared and
  used. See section [TBD] for details.
---

# Contexts

## Type Declaration

```
contextName: context
    SomeConstant: const int, 2;
    ValueA: recordName, {A[1], B[""]};
    ValueB: readonly float, 1.5;
    ValueC: {float*}, {1.0, 0.5, 1.0};
    ValueD: {A: int, -1; B: int;}, {B[2]}.
```

### As a Host

```
contextName: context  `If no mutualist exists, aliased values are independent.`
    MutualistA: mutualist otherContextName;
    ValueA[MutualistA(SomeFloat), 2.0],  `Alias mutualist value, default to 2.0.`
    ValueB[MutualistA(SomeBool)] readonly,
    ValueB: bool, false.
```

```
contextName: context  `Uses either existing mutualist value, neither, or binds both.`
    MutualistA: mutualist otherContextName;
    MutualistB: mutualist anotherContextName;
    ValueA[MutualistA(SomeFloat), MutualistB(OtherFloat), 2.0].
```

### As a Mutualist

```
contextName: context
    HostA: host otherContextName;
    ValueA[HostA(SomeFloat), 3.0],  `Alias host value, default to 3.0.`
    ValueB[HostA(SomeBool)] readonly,
    ValueC: int, -1.
```

```
contextName: context  `Binds two hosts' values through a value.`
    HostA: host otherContextName;
    HostB: host anotherContextName;
    ValueA[HostA(SomeFloat), HostB(OtherFloat), 3.0].
```

### Based on a Context

<pre><code><strong>otherContextName: context(contextName]  `Only inherits values/qualifiers, not use.`
</strong>    AdditionalValue: int, -1.
</code></pre>

### Based on a Record

```
contextName: context[recordName]
    NonRecordValueA: int, -1.
```

### Generic

```
contextName(TValue): context
    ValueA: TValue;
    ValueB: genericRecordName(TValue).
```

### With In-lined Value Aliasing

```
contextName: context
    ValueA: recordName;
    ValueAliasA[ValueA(A)],
    ValueAliasB[ValueB(B)].
```

### With Qualifiers

```
contextName: context
    ConstantA: const int, 0;
    ValueA: int, -1;
    ValueB: recordName, {A[1]};
    QualifierA: ValueA > ConstantA;
    QualifierB: Value < ValueB(A).
```

```
otherContextName: context[contextName]
    QualifierA: ValueA > ConstantA
```

## Accessing

### Setup

```
`Assume the following for all accessing code examples.`

contextName: context
    ValueA: int, -1;
    ValueB: string, "";
    ValueC: float, 0.0;
    ValueD: int, -1;
    ValueE: bool, false.

someContext: contextName;
```

### Retrieving

```
someContext(ValueA) = -1
```

```
someContext(ValueA, ValueB) = {-1, ""}
```

```
someContext!(ValueA, ValueB) = {0.0, -1, false}
```

```
someContext(...) = {-1, "", 0.0, =1, false}
```

### Setting

```
someContext(ValueA) is 2,
```

```
someContext(ValueA, ValueB) is otherContext(ValueA, ValueB),
```

```
someContext(ValueA, ValueB) is otherContext(ValueA[ValueC], ValueB[ValueD]),
```

```
someContext!(ValueA, ValueB) is {ValueC[3.5], ValueD[0], ValueE[true]},
```

```
someContext!(ValueA, ValueB) is {ValueC[3.5], ...},  `Match remaining values.`
```

```
someContext(...) is matchingContext,
```

```
someContext(...) is matchingRecord,  `Assign all value.`
```

```
someContext(...) is someRecord with contextMapping,
```

```
someContext(...) is someRecord where
{
    ValueA is RecordValueA,
    ValueB is RecordValueB
},
```

```
someContext(...) is {ValueA[1], ValueB[""], ...},  `Match remaining values.`
```

## Operators

```
someContext(ValueA, ValueB) is {ValueA[1], ValueB[""]},
```

### Await

```
await someContext,
```

```
await someContext with otherContext,
```

```
await someContext as contextAlias with otherContext,
```

### Deregistration

```
deregister someContext,
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
c ~ {ValueA[-1]},
```

```
c(ValueA, ValueB) ~ r(ValueB),
```

#### Strict

```
c = r,
```

```
c = {ValueA[-1], ValueB[""]},
```

```
c = {ValueA[-1], ...},  `Match remaining values.`
```

```
c(ValueA, ValueB) = {ValueA[-1], ValueB[""]},
```

```
c(ValueA, ValueB) = r(ValueA, ValueB),
```

### Registration

```
register someContext,
```

```
`Declare and register the variable.`
register someContext: contextName, {ValueA[1], ValueB[""]};

`All other declaration methods can also be used.`
```

## Variables

### Declaration

```
someContext: contextName;  `Declare with all default values.`
```

```
someContext: genericContextName(int); `Declare with all default values.`
```

```
someContext: contextName, {ValueA[1], ValueB[""]};  `Default unspecified values.`
```

```
someContext: genericContextName(int), {GenericValueA[1], NonGenericValueA[""]};
```

```
someContext: contextName, matchingContext;
```

```
someContext: contextName, matchingRecord;
```

```
someContext: contextName, someRecord with contextMapping;
```

```
someContext: contextName, someRecord where
{
    ValueA is RecordValueA,
    ValueB is RecordValueB
};
```

```
someContext: contextName, matchingRecord, HostA is otherContext;
```

```
someContext: contextName, matchingRecord, MutualistA is otherContext;
```
