---
description: >-
  The following program example demonstrates how "Hello World!" can be output
  upon program startup.
---

# Hello World

```
main: when initialized?
    await output: Console Output; as Registration,
    output(Messages) is "Hello World!".
```

```
`Alternative, condensed version.`

main: when initialized?
    run !: Console Output [ Messages["Hello World!"] ]; as Registration.
```
