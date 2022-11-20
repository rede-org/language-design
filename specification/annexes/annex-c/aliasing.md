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
