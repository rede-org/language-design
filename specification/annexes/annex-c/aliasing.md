# Aliasing

The following code examples demonstrate how a previously declared type can have an alternative name (an alias). See section \[TBD] for details.

## In General

```
aliasName: [typeName] 
    AliasA[MemberA], 
    AliasB[MemberB].
```

```
aliasName: [typeName] AliasA[MemberA], AliasB[MemberB].
```

```
aliasName: [typeName]... `Defaults all members to their same name in the alias.`
```

```
multiAliasName: [typeNameA, typeNameB]
    AliasA[MemberAA, MemberBA],
    AliasB[MemberAB, MemberBB].
```

## Contexts

```
aliasName: [someContextName]
    AliasA[PropertyA],
    AliasB[PropertyB] readonly.
```

```
aliasName: [someContextName]...
```

## Enums

```
aliasName: [someEnumName]
    AliasA[A],
    AliasB[B].
```

```
aliasName: [someEnumName]...
```

## Records

```
aliasName: [someRecordName]
    AliasA[ValueA] readonly,
    AliasB[ValueB].
```

```
aliasName: [someRecordName]...
```

## Use

### Context Awaiting

```
await someContext as aliasName,
```

### Variable Assignment

```
aliasedRecord = someRecord as aliasName,
```

### Variable Declaration

```
aliasedRecord: aliasName, someRecord;  `Implicit alias.`
```

```
nonAliasedRecord: recordName, aliasedRecord;  `Implicit reverse alias.`
```

```
`Alias someRecord as multiAliasName, then reverse alias to otherRecordName.`
otherRecord: otherRecordName, someRecord as multiAliasName;
```
