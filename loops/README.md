# loops

Loops: repeat A0 times, for each A0 in A1, repeat while.

```
use loops
```

It uses `flag` (its `libraries.toml`), installed with it.

`core` uses it first, right after the entries. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `repeat A0 times : A1` | Runs the line after the colon A0 times. | `repeat 3 times: say "hi"` |
| `for each A0 in A1 : A2` | Runs the line after the colon once for each item of the list A1, with the item in A0. | `for each n in [1, 2, 3]: say n * 2` |
| `repeat while A0 : A1` | Runs the line after the colon as long as A0 is true. Stops with an error after 100000 times. | `repeat while n < 5: n is n + 2` |
