# Aliasing

The following code examples demonstrate how a previously declared type can have an alternative name (an alias). See section \[TBD] for details.

## In General

```
aliasName: [originalTypeName] 
    AliasA[OriginalMemberA], 
    AliasB[OriginalMemberB].
```

```
aliasName: [originalTypeName]... `Defaults all members to the same name.`
```

## Contexts

```
aliasName: [someContextName]
    AliasA[PropertyA],
    AliasB[PropertyB].
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
    AliasA[ValueA],
    AliasB[ValueB].
```

```
aliasName: [someRecordName]...
```
