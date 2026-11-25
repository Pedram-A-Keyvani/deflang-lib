# errors

Errors: fail with A0, and A0, or if that fails, A1.

```
use errors
```

It uses `flag` (its `libraries.toml`), installed with it.

`core` uses it, right after `questions`. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `A0, or if that fails, A1` | Runs A0; if it stops with an error, runs A1 instead, with the error's message as `error`. | `say 1 / 0, or if that fails, say "can't"` |
| `fail with A0` | Stops the program with the message A0, a value like any other: "port " port " is taken". | `fail with "no " 1 + 1` |
