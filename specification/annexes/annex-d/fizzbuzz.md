---
description: >-
  The following program examples demonstrate how a fizzbuzz can be output for a
  given number.
---

# FizzBuzz

```
Input: readonly context Int.
Fizzbuzz: context {String*}.

Fizzbuzz for Application Inputs: <inputs>,
    when initialized?
        await <inputs(0) as Input, result: Fizzbuzz;>,
        run !: Console Output [ Messages[result] ] as Registration.

Evaluate Input as Fizzbuzz: <input, fizzbuzz>
    foreach i in !: Range(1, input)?
{
    Mod 15 :: when i % 15?
        fizzbuzz is fizzbuzz + "fizzbuzz";
    Mod 5 :: when i % 5,
        without Mod 15?
        fizzbuzz is fizzbuzz + "buzz";
    Mod 3 :: when i % 3,
        without Mod 15?
        fizzbuzz is fizzbuzz + "fizz";
    Otherwise :: default?
        fizzbuzz is fizzbuzz + i to String;
}
```
