# questions

Questions: A0 ?, is not ?, A0 that A1.

```
use questions
```

It uses `flag` (its `libraries.toml`), installed with it.

`core` uses it, right after `loops`. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `is not ?` | Flips the answer of the last question, like an else. | `is not ?` |
| `A0 ?` | Asks a question: the indented lines below run only if A0 is true. | `5 > 3 ?` |
| `A0 that A1` | Puts the value of A0 in front of A1 and runs it. | `2 that > 1` |
