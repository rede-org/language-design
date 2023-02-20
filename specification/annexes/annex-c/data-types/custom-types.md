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
        Value A: Int[Mutualist A(Some Int), 0];
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
        Value A: Int[Host A(Some Int), 0];
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

...

## Operators

{% tabs %}
{% tab title="All Data Types" %}

{% endtab %}

{% tab title="Context-Only" %}

{% endtab %}
{% endtabs %}

## Variables

...
