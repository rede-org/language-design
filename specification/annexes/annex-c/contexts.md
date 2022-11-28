# Contexts

The following code examples demonstrate how a context type can be declared and used. See section \[TBD] for details.

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

## Use

### Awaiting

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

```
c == r,
```

```
c == {ValueA[-1], ValueB[""]},
```

```
c == {ValueA[-1], ...},  `Match remaining values.`
```

```
c(ValueA, ValueB) == {ValueA[-1], ValueB[""]},
```

```
c(ValueA, ValueB) == r(ValueA, ValueB),
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

### Value Assignment

```
someContext(ValueA) = 2,
```

```
someContext(ValueA, ValueB) = {ValueA[1], ValueB[""]},
```

```
someContext(ValueA, ValueB) = otherContext(ValueA, ValueB),
```

```
someContext(ValueA, ValueB) = otherContext(ValueA[ValueC], ValueB[ValueD]),
```

```
someContext~(ValueA, ValueB) = {ValueC[3.5], ValueD[0], ValueE[true]},
```

```
someContext~(ValueA, ValueB) = {ValueC[3.5], ...},  `Match remaining values.`
```

```
someContext(...) = matchingRecord,  `Assign all value.`
```

```
someContext(...) = someRecord with contextMapping,
```

```
someContext(...) = someRecord where
{
    ValueA = RecordValueA,
    ValueB = RecordValueB
}
```

```
someContext(...) = {ValueA[1], ValueB[""], ...},  `Match remaining values.`
```

### Variable Declaration

```
someContext: contextName;  `Declare with all default values.`
```

```
someContext: contextName, {ValueA[1], ValueB[""]};
```

```
someContext: contextName, {ValueA[1], ValueB[""], ...};  `Default other values.`
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
    ValueA = RecordValueA,
    ValueB = RecordValueB
}
```

```
someContext: contextName, matchingRecord, HostA is otherContext;
```

```
someContext: contextName, matchingRecord, MutualistA is otherContext;
```

