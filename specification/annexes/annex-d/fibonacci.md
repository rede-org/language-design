---
description: >-
  The following program examples demonstrate how a fibonacci number can be found
  for a given number.
---

# Fibonacci

```
Find fibonacci for Application Inputs: <inputs>,
    when initialized?
        run !: Console Output [ Messages[inputs(0) to fibonacci result] ]
            as Registration.

Int to fibonacci Int: (i) ??
    i < 2 => i,
    default => i - 1 to fibonacci + (i - 2 to fibonacci).

Int to fibonacci result String: (i) => 
    "Fibonacci: \(i to fibonacci to String)".
```
