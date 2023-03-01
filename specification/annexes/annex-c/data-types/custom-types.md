---
description: >-
  The following code examples demonstrate how custom types can be declared and
  used. See section [TBD] for details.
---

# Custom Types

## Declaration

{% tabs %}
{% tab title="Basic" %}
```
`Declare a new type called "Special Int" to wrap around the built-in Int.`
`Default the value of this type to 0.`

Special Int: Int[0].
```
{% endtab %}

{% tab title="Composite" %}
```
`Declare a new type called "Some Record" to encapsulate 
a couple of values as a single data type.`

Some Record:
    {
        Value A: Int[0];
        Value B: Bool[false];
    }.
```

```
`Declare a new generic type called "Generic Record" to encapsulate 
a couple of values as a single data type, including a value whose 
type is generically defined as "TValue".`

Generic Record (TValue):
    {
        Generic Value: TValue;
        Other Value: Bool[false];
    }.
```

```
`Declare an anonymous type, as part of the variable declaration for a 
variable called "record", to encapsulate a couple of values 
as a single data type.`

record: {A: int[-1]; B: int;} [B[2]];
```
{% endtab %}

{% tab title="Constant" %}
```
`Declare a new type called "Constant Int" to define a constant 
type for the value of 2.`

Constant Int: const Int[2].
```

```
`Declare a new type called "Constant Record" to define a constant 
type for an encapsulation of a couple of values that cannot be changed.`

Constant Record:
    {
        Value A: Int[3];
        Value B: Bool[true];
    }.
```

```
`Declare a new type called "Some Record" to define a data 
type for an encapsulation of a couple of values, with a declared constant.`

Some Record:
    {
        Value A: Int[Constant A];
        Value B: Bool[false];
    },
    Constant A: Int[3].
```
{% endtab %}

{% tab title="Context" %}
```
`Declare a new context type called "Int Context" to 
wrap around the built-in Int as a context type.`

Int Context: context Int[0].
```

```
`Declare a new context type called "Some Context" to encapsulate 
a couple of values as a single context type.`

Some Context: context
    {
        Value A: Int[0];
        Value B: Bool[false];
    }.
```

```
`Declare a new context type called "Some Host" to encapsulate 
a couple of values as a single context type with an 
associated mutualist context of the type "Other Context".`

Some Host: context
    {
        `Link to Mutualist A's Some Int (if it exists), otherwise 
            default to 0.`
        Value A: Int[0], Mutualist A(Some Int);
        Value B: Bool[false];
    },
    Mutualist A: mutualist Other Context.
```

```
`Declare a new context type called "Some Mutualist" to encapsulate 
a couple of values as a single context type with an 
associated host context of the type "Other Context".`

Some Mutualist: context
    {
        `Link to Host A's Some Int and default its value to 0.`
        Value A: Int[0], Host A(Some Int);
        Value B: Bool[false];
    },
    Host A: host Other Context.
```
{% endtab %}

{% tab title="Readonly" %}
```
`Declare a new readonly type called "Readonly Int" to 
wrap around the built-in Int as a value that cannot be changed 
after the instance of the type has been created.`

Readonly Int: readonly Int[0].
```

```
`Declare a new type called "Readonly Record" to encapsulate 
a couple of values that cannot be changed after an instance of 
the type has been created.`

Readonly Record: readonly 
    {
        Value A: Int[0];
        Value B: Bool[false];
    }.
```

```
`Declare a new type called "Partial Readonly" to encapsulate 
a couple of values, one of which cannot be changed after an instance of 
the type has been created.`

Partial Readonly: 
    {
        Value A: readonly Int[0];
        Value B: Bool[false];
    }.
```

```
`Declare a new readonly context type called "Readonly Context" to 
wrap around the built-in Int as a context value that cannot be changed 
after the instance of the type has been created.`

Readonly Context: readonly context Int[0].
```
{% endtab %}
{% endtabs %}

### With Casts

```
`Declare a new type called "Some Record" with defined casting to an Int.

Some Record:
    {
        Value A: Int[0];
        Value B: Bool[false];
    },
    this to Int: () => this(Value A).
```

### With Modifiers

```
`Declare a new type called "Special Int" with modifiers to adjust its value.`
Special Int: Int[0],
    reset this: () | this is 0;
    update this with int: (i) | this is this + i.
```

```
`Declare a new type called "Some Record" with modifiers to adjust its values.`

Some Record:
    {
        Value A: Int[0];
        Value B: Bool[false];
    },
    reset this: () | 
        this(Value A) is 0, 
        this(Value B) is false;
    update this with int: (i) | 
        this(Value A) is i,
        this(Value B) is i > 10.
```

### With Operators

```
`Declare a new type called "Some Record" with functionality 
for the '+' operator being defined.`

Some Record:
    {
        Value A: Int[0];
        Value B: Bool[false];
    },
    this + Int: (i) => 
        {
            Value A[this(Value A) + i],
            Value B[this(Value B)]
        }.
```

### With Qualifiers

```
`Declare a new type called "Special Int" with a qualifier to specify whether 
the int is even.`
Special Int: Int[0],
    this is even: () => this % 2 = 0.
```

```
`Declare a new type called "Some Record" with a qualifier to specify 
whether the record is valid with a specified limit.`

Some Record:
    {
        Value A: Int[0];
        Value B: Bool[false];
    },
    this is valid for limit Int: (limit) => this(Value A) <= limit.
```

## Accessing

### Setup

```
`Assume the following for all accessing code examples.`

Record Name: 
    {
        A: int[-1];
        B: int[0];
    }.

some record: Record Name, {B[2]};
```

### Retrieving

```
some record (A) = -1
```

```
some record (A, B) = {-1, 2}
```

```
some record (...) = {-1, 2}
```

```
some record !(A) = 2
```

### Setting

```
some record (A) is 2,
```

```
some record (A, B) is {A[1], B[""]},
```

```
some record (A, B) is other record (A, B),
```

```
some record (A, B) is other record (A[C], B[D]),
```

```
some record !(A) is {B[3]},
```

```
some record !(A) is {...},  `Match remaining values.`
```

```
some record (...) is matching record,  `Assign all values.`
```

```
some record (...) is other record with record mapping,
```

```
some record (...) is other record where
{
    A is OtherA,
    B is OtherB
},
```

```
some record (...) is {A[1], ...},  `Match remaining values.`
```

## Operators

{% tabs %}
{% tab title="Basic Types" %}
By default, a custom type that wraps an existing type inherits the operators of the existing type, including those of [built-in types](built-in-types.md). Operators declared in the declaration of a type override any matching inherited operator.
{% endtab %}

{% tab title="Composite/Context Types" %}
### Difference

```
some record: {A: int[-1]; B: int;}, {B[2]};
other record: {A: int, 0;}, { };

some record - other record = {B[2]}
```

```
Record Name:
{
    A: int[0];
    C: int[-1];
}.

some record: {A: int[-1]; B: int;}, {B[2]};

some record - Record Name = {B[2]}
```

### Equality

#### Setup

```
`Assume the following for all equality code examples.`

Context Name: context
    {
        A: int[-1];
        B: string[""];
    }.

Record Name:
    {
        A: int[-1];
        B: string[""];
    }.

c: Context Name;
r: Record Name;
```

#### Approximate

```
r ~ {A[-1]},
```

```
r (A, B) ~ c (B),
```

#### Strict

```
r = c,
```

```
r = {A[-1], B[""]},
```

```
r = {A[-1], ...},  `Match remaining values.`
```

```
r (A, B) = {A[-1], B[""]},
```

```
r (A, B) = c (A, B),
```

### Intersection

```
some record: {A: int[-1]; B: int;}, {B[2]};
other record: {A: int[0];}, { };

some record % other record = {A[-1]}
```

```
Record Name:
{
    A: int, 0;
    C: int -1;
}.

some record: {A: int[-1]; B: int;};

some record % Record Name = {A[-1]}
```

### Union

```
some record: {A: int[-1]; B: int[0];}, {B[2]};
other record: {A: int[0]; C: int[0];}, { };

some record + other record = {A[-1], B[2], C[0]}
```

```
Record Name:
{
    A: int[0];
    C: int[-1];
}.

some record: {A: int[-1]; B: int;}, {B[2]};

some record + Record Name = {A[-1], B[2], C[-1]}
```
{% endtab %}

{% tab title="Context-Only" %}
### Await

```
await some context,
```

```
await <some context, other context>,
```

```
await <some context as Context Alias, other context>,
```

```
await <Context Name [A[1]], some context: Context Name [A[2]];>,
```

### Deregistration

```
deregister some context,
```

### ID Retrieval

```
Some operation for Context Name and Other Context Name: <a, b>
    when a' = b(some id)?
        `Do something`.
```

```
Some operation for Context Name and Other Context Name: <a, b>?
    b(some id) is a'.
```

### Registration

```
register some context,

`or, for with an ID:`
register some context for some id,
```

```
`Register a new context.`
register Context Name [A[1], B[""]],

`or, for with an ID:`
register Context Name [A[1], B[""]] for some id,

`All other declaration methods can also be used.`
```

```
`Declare and register a new context.`
register some context: Context Name [A[1], B[""]];

`or, for with an ID:`
register some context: Context Name [A[1], B[""]]; for some id,

`All other declaration methods can also be used.`
```
{% endtab %}
{% endtabs %}

## As Variables

Basic types that wrap existing types have variables that are assigned/declared the same as the existing type's variables would be. Composite/Context types are assigned/declared as follows.

### Assignment

```
some record is {ValueA[1], ValueB[""]},
```

```
some record is {ValueA[1], ...},  `Match (default)remaining values.`
```

### Declaration

```
some record: Record Name;  `Declare with all default values.`
```

```
some record: Generic Record Name(int); `Declare with all default values.`
```

```
some record: Record Name [A[1], B[""]];  `Default any unspecified values.`
```

```
some record: Generic Record Name(int) [GenericA[1], NonGenericA[""]];
```

```
some record: Record Name [matching record];
```

```
some record: Record Name [matching context];
```

```
`Anonymous record composed of two unioned record types.
 Initialized values specified by unioned record instances.`
some record: Record Name A + Record Name B [record a + record b];
```

```
`Anonymous record defined by the initialization value.`
some record: var [record a + {C[1]}];
```

```
some record: Record Name [other record with Record Mapping];
```

```
some record: Record Name [other record where
{
    A is OtherA,
    B is OtherB
}];
```

#### Context-Only Declarations

```
mutualist context: Context Name [matching record, HostA is other context];
```

```
host context: Context Name [matching record, MutualistA is other context];
```
