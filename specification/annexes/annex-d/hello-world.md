---
description: >-
  The following program examples demonstrate how "Hello World!" can be output
  upon program startup.
---

# Hello World

```
`Simplest version.`

Main: when initialized?
    run "Hello World!" as Console Message.
```

```
`Alternative, explicit Console Output version.`

Main: when initialized?
    await output: Console Output; as Registration,
    output(Messages) is "Hello World!".
```

```
`Alternative, explicit Console Output version; condensed.`

Main: when initialized?
    run !: Console Output [ Messages["Hello World!"] ]; as Registration.
```
