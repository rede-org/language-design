---
description: >-
  The following code examples demonstrate the built-in primitive types offered
  by the language and how they can be used. See section [TBD] for details.
---

# Primitives

## Primitives

| Logic | Text   | Numeric | Core |
| ----- | ------ | ------- | ---- |
| Bool  | Char   | Byte    | Guid |
| Tril  | String | Ubyte   | Id   |
|       |        | Short   | Type |
|       |        | UShort  |      |
|       |        | Int     |      |
|       |        | UInt    |      |
|       |        | Long    |      |
|       |        | Ulong   |      |
|       |        | Float   |      |
|       |        | Double  |      |
|       |        | Decimal |      |
|       |        | Range   |      |

## Details

{% tabs %}
{% tab title="String" %}
```
formatted text: String ["a formatted message: \(some value to string)"];
```
{% endtab %}

{% tab title="Range" %}
```
r: Range [0, 2];  `Range from minimum 0 to maximum 2, being 0, 1, 2.`
```
{% endtab %}

{% tab title="Id" %}
```
some id: Id [@some context];  `IDs are only associated with contexts.`
```

```
some operation for Context Name when in {*Context Name*}: 
    <context, bucket>,
    when bucket(@context?)?
        `Operation logic.`
```
{% endtab %}

{% tab title="Type" %}
```
`Any type name can be used as a type value, in the same way 4 is an int.`
t: Type [Some Context Name];
```

```
`Strings can be cast to a type, throwing an error if it cannot.`
t: Type ["Some Context Name"];
```

```
`Retrieve an instance type with the prime operator.`
t: Type [instance'];
```

```
t(Name) `"Some Context Name"`
t(Value Names) `{ "Value A", "Value B" }`
t(Contracts) `{ Some Contract Name, Other Contract Name }`
```

```
`Instances can be built from types.`

instance: some type;  `Creates an instance of the type value with defaults.`
instance: some type [other instance (Value A)];  `Errors if not matching.`

`Nothing can really be done with these instances, but evaluating them 
    can result in an operation working with them with strong typing.`
await <instance>,
```

```
`Equality checks.`

instance' = some type
instance' = Type Name

instance' < some ancestor type
instance' > some descendent type
instance' ~ some contract type
```
{% endtab %}
{% endtabs %}

## As Variables

### Assignment

```
some int is 1,
```

### Declaration

```
some int: int [1];
```

```
some int: int [a + b];
```
