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

### As a Mutualist

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

### Variable Assignment



