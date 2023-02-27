---
description: >-
  The following code examples demonstrate the built-in types offered by the
  language and how they can be used. See section [TBD] for details.
---

# Built-in Types

## Collections

{% tabs %}
{% tab title="Sets" %}
## Declaration

```
Set Name: {*Int}.
```



## Accessing

### Containment

```
some set: {*Int}, {1, 2, 3};
some set(1?) = true
some set(4?) = false
```

```
some set: {*Int}, {1, 2, 3};
some set(1?, 4?) = {true, false}
```

### Retrieving

```
some set: {*Int}, {1, 2, 3};
some set(...) = {1, 2, 3}  `Total collection accessor.`
```



## Operators

### Count

```
|{1, 2, 3} as {*Int}| = 3
```

```
|some set| = 5
```

### Difference (Remove Elements)

```
{1, 2, 3} as {*Int} - {2, 3, 4, 5} = {1}
```

```
{2, 3, 4, 5} as {*Int} - {1, 2, 3} = {4, 5}
```

### Equality

#### Setup

```
`Assume the following for all equality code examples.`

some set: {*Int}, {1, 2, 3};
```

#### Approximate

```
some list: {Int*}, {1, 2, 2, 3};
some set ~ some list
```

```
some dict: {Int: Int, -1}, {1[1], 2[1], 3[0]};
some set ~ some dict
```

#### Strict

```
some set = {1, 2, 3}
```

```
some set = {1, 2, ...}  `Match remaining values.`
```

### Intersection

```
{1, 2, 3} as {*Int} % {2, 3, 4, 5} = {2, 3}
```

```
{2, 3, 4, 5} as {*Int} % {1, 2, 3, 3} = {2, 3}
```

### Union (Appending)

```
{1, 2} as {*Int} + {2, 3} = {1, 2, 3}
```

```
{2, 3} as {*Int} + {1, 2} = {2, 3, 1}
```
{% endtab %}

{% tab title="Tuples" %}
## Declaration

```
Tuple Name: {Int, Int, Bool}.
```



## Accessing

### Retrieving

```
some tuple: {Int, Int, Bool}, {1, 2, false};
some tuple (0) = 1
```

```
some tuple: {Int, Int, Bool}, {1, 2, false};
some tuple (0, 2) = {1, false}
```

```
some tuple: {Int, Int, Bool}, {1, 2, false};
some tuple (-1) = {false}
```

```
some tuple: {Int, Int, Bool}, {1, 2, false};
some tuple !(0) = {2, false}
```

```
some tuple: {Int, Int, Bool}, {1, 2, false};
some tuple (...) = {1, 2, 3}  `Total collection accessor.`
```

```
some tuple: {Int, Int, Bool}, {1, 2, false};
some tuple ((0, 2]) = {2, false}
```

```
some tuple: {Int, Int, Bool}, {1, 2, false};
some tuple !((0, 2]) = {1}
```

### Setting

```
some tuple (0) is 1,
```

```
some tuple (0, 2) is {1, true},
```

```
some tuple ([0, 2]) is {1, 3, true}, `Range must be within the Tuple's bounds.`
```



## Operators

### Count

```
|{1, 2, false}| = 3
```

```
|some tuple| = 5
```

### Difference (by Type Matching)

```
{1, 2, false} - {3, true} = {2}
```

```
{2, 3, 4, 5} - {1, 2} = {4, 5}
```

### Equality

#### Setup

```
`Assume the following for all equality code examples.`

some tuple: {Int, Int, Bool}, {1, 2, false};
```

#### Approximate

```
other tuple: {Bool, Int, Int}, {false, 1, 2};
some tuple ~ other tuple
```

#### Collective

```
{1, 1} &= 1  `All elements match the right-side element(s).`
{1, 2, 2, 1} &= {1, 2}
```

```
{true, true} &= true
{false, false} &= false
```

```
someTuple |= 1  `At least one element matches the right-side element(s).`
someTuple |= {1, true}
```

```
{true, false, 0} |= true
{true, 1, false} |= false
```

#### Strict

```
some tuple = {1, 2, false}
```

```
some tuple = {1, 2, ...}  `Match remaining values.`
```

### Intersection (by Type Matching)

```
{1, 2, false} % {2, 3, 4, 5} = {1, 2}
```

```
{2, 3, 4, 5} % {1, 2, 3, 3} = {2, 3, 4, 5}
```

### Union

```
{1, 2} + {2, false, 3} = {1, 2, 2, false, 3}
```

```
{2, 3} + {1, 2, true} = {2, 3, 1, 2, true}
```
{% endtab %}

{% tab title="Lists" %}
## Declaration

```
List Name: {Int*}.
```



## Accessing

### Containment

```
some list: {Int*}, {1, 2, 3};
some list (0?) = true    `The index 0 has a value in the list.`
some list (3?) = false  `The index 3 does not have a value in the list.`
```

```
some list: {Int*}, {1, 2, 3};
some list (0?, 3?) = {true, false}  `Whether there is a value for each index.`
```

```
some list: {Int*}, {1, 2, 3};
some list (0 ? -1) = 1  `Provide the value at index 0, or default to -1.`
some list (3 ? -1) = -1
```

```
some list: {Int*}, {1, 2, 3};
some list (0 ? -1, 3 ? -1) = {1, -1}
```

```
some list: {Int*}, {1, 2, 3};
some list ([1, 4)?) = {true, true, false}  `Check for indices in range [1, 4).`
```

```
some list: {Int*}, {1, 2, 3};
some list ([1, 4) ? -1) = {2, 3, -1}
```

### Retrieving

```
some list: {Int*}, {1, 2, 3};
some list (0) = 1
```

```
some list: {Int*}, {1, 2, 3};
some list (0, 2) = {1, 3}
```

```
some list: {Int*}, {1, 2, 3};
some list (-1) = {3}
```

```
some list: {Int*}, {1, 2, 3};
some list !(0) = {2, 3}
```

```
some list: {Int*}, {1, 2, 3};
some list (...) = {1, 2, 3}  `Total collection accessor.`
```

```
some list: {Int*}, {1, 2, 3};
some list ((0, 2]) = {2, 3}
```

```
some list: {Int*}, {1, 2, 3};
some list !((0, 2]) = {1}
```

### Setting

```
some list (0) is 1,
```

```
some list (0, 2) is {1, 3},
```

```
some list ([1, 4]) is {1, 3, 4, 2},
```



## Operators

### Count

```
|some list| = 5
```

```
|{1, 2, 3}| = 3
```

### Difference (Remove Elements)

```
{1, 2, 3, 3} - {2, 3, 4, 5} = {1, 3}
```

```
{2, 3, 4, 5} - {1, 2, 3, 3} = {4, 5}
```

### Equality

#### Setup

```
`Assume the following for all equality code examples.`

some list: {Int*}, {1, 2, 2, 3};
```

#### Approximate

```
some set: {Int}, {1, 2, 3};
some list ~ some set
```

```
some dict: {Int: Int, -1}, {1[1], 2[1], 3[0]};
some list ~ some dict
```

#### Collective

```
{1, 1} &= 1  `All elements match the right-side element(s).`
{1, 2, 2, 1} &= {1, 2}
```

```
{true, true} &= true
{false, false} &= false
```

```
some list |= 1  `At least one element matches the right-side element(s).`
some list |= {1, 3}
```

```
{true, false} |= true
{true, false} |= false
```

#### Strict

```
some list = {1, 2, 2, 3}
```

```
some list = {1, 2, ...}  `Match remaining values.`
```

### Intersection

```
{1, 2, 3, 3} % {2, 3, 4, 5} = {2, 3}
```

```
{2, 3, 4, 5} % {1, 2, 3, 3} = {2, 3}
```

```
{1, 2, 3, 3} % {3, 0, 1, 3} = {1, 3, 3}
```

### Union (Appending)

```
{1, 2} + {2, 3} = {1, 2, 2, 3}
```

```
{2, 3} + {1, 2} = {2, 3, 1, 2}
```
{% endtab %}

{% tab title="Dictionaries" %}
## Declaration

```
Dict Name: {String: Int, -1}.
```



## Accessing

### Containment

```
some dict: {String: Int, -1}, {"A"[0], "B"[1], "C"};

some dict ("A"?) = true
some dict ("D"?) = false
```

```
some dict: {String: Int, -1}, {"A"[0], "B"[1], "C"};

some dict ("A"?, "D"?) = {true, false}
```

```
some dict: {String: Int, -1}, {"A"[0], "B"[1], "C"};

some dict ("A" ? -1) = 0
some dict ("D" ? -1) = -1
```

```
some dict: {String: Int, -1}, {"A"[0], "B"[1], "C"};

some dict("A" ? -1, "D" ? -1) = {0, -1}
```

```
some dict: {String: Int, 0}, {"A"[1], "B"[2], "C"};
keys: {string}, {"A", "B", "C", "D"}

`Provide default for any key not found.`
some list: {Int*}, some dict (keys(...) ? -1);
some list = {1, 2, 0, -1}
```

```
some dict: {String: Int, 0}, {"A"[1], "B"[2], "C"};

some record: var, some dict(ValueA["A" ? -1], ValueD["D" ? -1]);
some record = {ValueA[1], ValueD[-1]}
```

### Retrieving

```
some dict: {String: Int, -1}, {"A"[0], "B"[1], "C"};
some dict ("C") = -1
```

```
some dict: {String: Int, -1}, {"A"[0], "B"[1], "C"};
some dict !("C") = {"A"[0], "B"[1]}
```

```
some dict: {String: Int, -1}, {"A"[0], "B"[1], "C"};
some dict ("A", "C") = {0, -1}
```

```
some dict: {String: Int, -1}, {"A"[0], "B"[1], "C"};
some dict (ValueA["A"], ValueB["C"]) = {ValueA[0], ValueB[-1]}
```

```
some dict: {String: Int, -1}, {"A"[0], "B"[1], "C"};
some dict (...) = {0, 1, -1}  // Total collection accessor.
```

### Setting

```
some dict ("A") is 1,
```

```
some dict ("A", "B") is {1, 3},
```



## Operators

### Count

```
|some dict| = 5
```

```
|{"A"[0], "B"[1], "C"}| = 3
```

### Difference (Remove Elements)

```
{"A"[0], "B"[1], "C"[2]} - {"A", "D"} = {"B"[1], "C"[2]}
```

```
{"A"[3], "B"[4], "C"[5]} - {"A"[0], "B"[1]} = {"C"[5]}
```

### Equality

#### Setup

```
`Assume the following for all equality code examples.`

some dict: {Int: Int, -1}, {1[1], 2[1], 3[0]};
```

#### Approximate

```
some list: {Int*}, {1, 2, 2, 3};
some dict ~ some list
```

```
some set: {Int}, {1, 2, 3};
some dict ~ some set
```

#### Strict

```
some dict = {1[1], 2[1], 3[0]}
```

```
some dict = {1[1], 2[1], ...}  `Match remaining keys and their values.`
```

### Intersection

```
{"A"[0], "B"[1], "C"[2]} % {"A", "D"} = {"A"[0]}
```

```
{"A"[3], "B"[4], "C"[5]} % {"A"[0], "B"[1]} = {"A"[3], "B"[4]}
```

```
{"A"[0], "B"[1], "C"[2]} % {"B", "A"} = {"A"[0], "B"[1]}
```

### Union (Appending)

```
`Default int value is assigned to "D" through the union.`
{"A"[0], "B"[1], "C"[2]} + {"A", "D"} = {"A"[0], "B"[1], "C"[2]. "D"[0]}
```

```
some dict: {String: Int, -1}, {"A"[0], "B"[1], "C"[2]};
some dict + {"A", "D"} = {"A"[0], "B"[1], "C"[2]. "D"[-1]}
```

```
{"A"[0], "B"[1]} + {"A"[1], "C"[1]} = {"A"[0], "B"[1], "C"[1]}
```

```
Dict Name: {String: Int, -1}.
{"A", "C"} as Dict Name + {"A"[0], "B"[1]} = {"A"[-1], "B"[1], "C"[-1]}
```
{% endtab %}

{% tab title="Buckets" %}
\*Describes Buckets.
{% endtab %}
{% endtabs %}

## Primitives

\*Describe Rede primitives.
