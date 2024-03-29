---
description: >-
  The following code examples demonstrate how custom types can be declared and
  used. See section [TBD] for details.
---

# Custom Types

## Type Declaration

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
`Declare a new type called "Some Record" to encapsulate 
a couple of values as a single data type and to fulfill the 
contract "Valuable".`

Some Record [Valuable]:
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
`Declare a new generic type whose generic type parameter is limited to 
types that fulfill specific contracts.`

Generic Record (TValue [Some Contract, Other Contract] ):
    {
        Generic Value: TValue;
        Other Value: Bool[false];
    }.
```

```
`Declare an anonymous type, as part of the variable declaration for a 
variable called "record", to encapsulate a couple of values 
as a single data type.`

record: {A: Int[-1]; B: Int;} [B[2]];
```

```
`Declare a new type called "Alias Record" that replaces some of its 
ancestor type's values, essentially aliasing them. Replacing value types 
must be convertible to/from their replaced value types.`

Alias Record: Some Record
    {
        Alias A: replaces Value A;
        Alias B: Int[0] replaces Value B;
    }.
```

```
`Declare a new type called "Extending Record" that extends its 
ancestor type with new values.`

Extending Record: Some Record
    {
        Value C: String[""];
        Value D: Bool[true];
    }.
```

```
`Declare a new type called "Focused Record" that removes a value 
from its ancestor type.

Focused Record: Some Record
    {
        !: replaces Value B;
    }
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
`Declare a new context type called "Some Context" to encapsulate 
a couple of values as a single context type and to fulfill the 
contract "Valuable".`

Some Context [Valuable]: context
    {
        Value A: Int[0];
        Value B: Bool[false];
    }.
```

```
`Declare a new generic type whose generic type parameter is limited to 
types that fulfill specific contracts.`

Generic Context (TValue [Some Contract, Other Contract] ): context
    {
        Generic Value: TValue;
        Other Value: Bool[false];
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

```
`Declare a new type called "Alias Context" that replaces some of its 
ancestor type's values, essentially aliasing them. Replacing value types 
must be convertible to/from their replaced value types.`

Alias Context: context Some Context
    {
        Alias A: replaces Value A;
        Alias B: Int[0] replaces Value B;
    }.
```

```
`Declare a new type called "Extending Context" that extends its 
ancestor type with new values.`

Extending Context: context Some Context
    {
        Value C: String[""];
        Value D: Bool[true];
    }.
```

```
`Declare a new type called "Focused Context" that removes a value 
from its ancestor type.

Focused Context: context Some Context
    {
        !: replaces Value B;
    }
```
{% endtab %}

{% tab title="Contract" %}
```
`Declare a new contract type called "Valuable" to 
encapsulate a couple of values for contractual use (abstraction) of 
any types that fulfill the contract.`

Valuable: contract
    {
        Value A: Int[0];
        Value B: Bool[false];
    }.
```

```
`Declare a new generic contract.`

Generic Contract (TValue):
    {
        Generic Value: TValue;
        Other Value: Bool[false];
    }.
```

```
`Declare a new type called "Alias Contract" that replaces some of its 
ancestor contract type's values, essentially aliasing them. 
Replacing value types must be convertible to/from their replaced value types.`

Alias Contract: contract Valuable
    {
        Alias A: replaces Value A;
        Alias B: Int[0] replaces Value B;
    }.
```

```
`Declare a new type called "Extending Contract" that extends its 
ancestor contract type with new values.`

Extending Contract: contract Valuable
    {
        Value C: String[""];
        Value D: Bool[true];
    }.
```

```
`Declare a new type called "Focused Contract" that removes a value 
from its ancestor contract type.

Focused Contract: contract Valuable
    {
        !: replaces Value B;
    }
```
{% endtab %}

{% tab title="Enum" %}
```
`Declare a new type called "Some Enum" to encapsulate 
named instances as members of an enum.`

Some Enum: [Byte]
    {
        A[0],
        B[1],
        C[2]
    }.
```

```
`Declare a new type called "Alias Enum" that wraps around an ancestor 
enum's members, essentially aliasing them.`

Alias Enum: [Some Enum]
    {
        First[A],
        Second[B],
        Third[C]
    }.
```

```
`Declare a new type called "Extending Enum" that provides additional 
members pointing to the members of its ancestor enum.`

Extending Enum: [Some Enum]
    {
        First[A],
        Second[B],
        Third[C],
        Fourth[C]
    }.
```

```
`Declare a new type called "Focused Enum" that leaves out some of 
the members of its ancestor enum.`

Focused Enum: [Some Enum]
    {
        First[A],
        Second[B]
    }.
```
{% endtab %}
{% endtabs %}

### Flags

{% tabs %}
{% tab title="Constant" %}
```
`Declare a new type called "Constant Int" to define a constant 
type for the value of 2.`

Constant Int: const Int[2].
```

```
`Declare a new type called "Constant Record" to define a constant 
type for an encapsulation of a couple of values that cannot be changed.`

Constant Record: const 
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
    Constant A: const Int[3].
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

### Decorators

{% tabs %}
{% tab title="Modifiers" %}
```
`Declare a new type called "Special Int" with modifiers to adjust its value.`
Special Int: Int[0],
    reset this: () | this is 0;
    update this with int: (i) | this is this + i.
```

```
`Declare a new type called "Special Int" with a modifier that adjusts 
    its value in accordance with an in-line mapping that has 
    conditional sub-mappings.`

Special Int: Int[0],
    reset this: () | 
        this is this -> (Special Int => Special Int) 
            [
                (i) ?? 
                    i % 2 = 1 => 1,
                    i = 0 => 0,
                    default => 2
            ].
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
    update this with Int: (i) | 
        this(Value A) is i,
        this(Value B) is i > 10.
```

#### With Identifiers

```
Some Record:
    {
        Value A: Int[0];
        Value B: Bool[false];
    },
    Reset :: reset this: () | 
        this(Value A) is 0, 
        this(Value B) is false;
    Update :: update this with Int: (i) | 
        this(Value A) is i,
        this(Value B) is i > 10.
```

#### With Replacements

```
Alias Record: Some Record,
    refresh this: () replaces Reset | 
        reset this;
    set this for Int: (i) replaces Update | 
        update this with i.
```

#### With Removals

```
Focused Record: Some Record,
    !: replaces Reset;
    !: replaces Update.
```
{% endtab %}

{% tab title="Operators" %}
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

```
`Declare a new type called "Special Int" with functionality 
    for the '+' operator that uses a conditional to 
    determine the result.`

Special Int: Int[0],
    this + Int: (i) ?? 
        i % 2 = 1 => this + 1,
        i = 0 => this,
        default => this + 2.
```

#### With Identifiers

```
Some Record:
    {
        Value A: Int[0];
        Value B: Bool[false];
    },
    Add :: this + Int: (i) => 
        {
            Value A[this(Value A) + i],
            Value B[this(Value B)]
        }.
```

#### With Removals

```
Focused Record: Some Record,
    !: replaces Add => this.
    `A return must be provided to support the base's use with generics.`
```

#### With Replacements

```
Other Record: Some Record,
    this + Int: (i) replaces Add => 
        {
            Value A[this(Value A) + i],
            Value B[(this(Value A) + i) > 10]
        }.
```
{% endtab %}

{% tab title="Qualifiers" %}
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

```
`Declare a new type called "Some Record" with a qualifier to specify 
whether the record is valid with a specified limit, per a conditional 
defined by another value of the record.`

Some Record:
    {
        Value A: Int[0];
        Value B: Bool[false];
    },
    this is valid for limit Int: (limit) ??
        this(Value B) => this(Value A) <= limit,
        default => true.
```

#### With Identifiers

```
Some Record:
    {
        Value A: Int[0];
        Value B: Bool[false];
    },
    is valid :: this is valid for Int: (limit) => 
        this(Value A) <= limit.
```

#### With Removals

```
Focused Record: Some Record,
    !: replaces Is Valid => false.
    `A return must be provided to support the base's use with generics.`
```

#### With Replacements

```
Alias Record: Some Record,
    this is qualified with Int: (limit) replaces Is Valid => 
        this is valid for limit.
```
{% endtab %}
{% endtabs %}

## Accessing

### Setup

```
`Assume the following for all accessing code examples.`

Record Name: 
    {
        A: Int[-1];
        B: Int[0];
    }.

some record: Record Name, { B[2] };
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
some record (A, B) is {1, ""},
```

```
some record (A, B) is other record (A, B),
```

```
some record (A, B) is other record (A[C], B[D]),
```

```
some record !(A) is { B[3] },  `Assign specific remaining values.`
```

```
some record (...) is matching record,  `Assign all values.`
```

```
some record (...) is other record to Record Name,  `Assign after mapping.`
```

```
some record (...) is {A[1], ...},  `Match remaining values.`
```

## Operators

{% tabs %}
{% tab title="Basic Types" %}
By default, a custom type that wraps an existing type inherits the operators of the existing type, including those of [built-in types](built-in-types/). Operators declared in the declaration of a type override any matching inherited operator.
{% endtab %}

{% tab title="Composite/Context Types" %}
### Difference

```
some record: { A: Int[-1]; B: Int; } [ B[2] ];
other record: { A: Int[0]; };

some record - other record = { B[2] }
```

```
Record Name:
{
    A: Int[0];
    C: Int[-1];
}.

some record: { A: Int[-1]; B: Int; } [ B[2] ];

some record - Record Name = { B[2] }
```

### Equality

#### Setup

```
`Assume the following for all equality code examples.`

Context Name: context
    {
        A: Int[-1];
        B: String[""];
    }.

Record Name:
    {
        A: Int[-1];
        B: String[""];
    }.

c: Context Name;
r: Record Name;
```

#### Approximate

```
r ~ { A[-1] },
```

```
r(A, B) ~ c(B),
```

#### Strict

```
r = c,
```

```
r = { A[-1], B[""] },
```

```
r = { A[-1], ... },  `Match remaining values.`
```

```
r (A, B) = { A[-1], B[""] },
```

```
r (A, B) = c (A, B),
```

### Intersection

```
some record: { A: Int[-1]; B: Int; } [ B[2] ];
other record: { A: Int[0]; }, { };

some record % other record = { A[-1] }
```

```
Record Name:
{
    A: Int, 0;
    C: Int -1;
}.

some record: { A: Int[-1]; B: Int; };

some record % Record Name = { A[-1] }
```

### Union

```
some record: { A: Int[-1]; B: Int[0]; }, { B[2] };
other record: { A: Int[0]; C: Int[0]; }, { };

some record + other record = { A[-1], B[2], C[0] }
```

```
Record Name:
{
    A: Int[0];
    C: Int[-1];
}.

some record: { A: Int[-1]; B: Int; } [ B[2] ];

some record + Record Name = { A[-1], B[2], C[-1] }
```
{% endtab %}
{% endtabs %}

## As Variables

Basic types that wrap existing types have variables that are assigned/declared the same as the existing type's variables would be. Composite/Context types are assigned/declared as follows.

### Assignment

```
some record is {Value A [1], Value B [""]},
```

```
some record is {Value A [1], ...},  `Match (default) remaining values.`
```

#### Context-Only Assignment

```
mutualist context <= Host A is another context,
```

```
host context <= Mutualist A is another context,
```

### Declaration

```
some record: Record Name;  `Declare with all default values.`
```

```
some record: Generic Record Name(int); `Declare with all default values.`
```

```
some record: Record Name [ A[1], B[""] ];  `Default any unspecified values.`
```

```
some record: Generic Record Name(int) [ Generic A [1], NonGeneric A [""] ];
```

```
some record: Record Name [matching record];
```

```
some record: Record Name [matching context];
```

```
`Anonymous record composed of two unioned record types.`
some record: Record Name A + Record Name B [record A + record B];
```

```
some record: Record Name [other record to Record Name];  `Explicit mapping.`
```

#### Context-Only Declarations

```
mutualist context: Context Name [matching record] <= HostA is other context;
```

```
host context: Context Name [matching record] <= MutualistA is other context;
```
