# values

Values: A0 is A1, A0 if A1 otherwise A2, A0 means A1.

```
use values
```

It uses `flag` (its `libraries.toml`), installed with it.

`core` uses it, right after `errors`. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `A0 is A1` | Stores the value of A1 under the name A0. | `x is 2 + 3` |
| `A0 if A1 otherwise A2` | A0 when A1 is true, otherwise A2. Only the part that is chosen runs. | `175 / 100 if 175 > 3 otherwise 175` |
| `A0 means A1` | From now on, the words A0 are read as A1. | `tiny means 0.001` |
