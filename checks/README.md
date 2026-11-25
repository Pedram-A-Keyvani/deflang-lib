# checks

Checks of a list's items: every one of them (`each of them is`), or one of them (`one of … is`), which then becomes `it`.

```
use checks
```

It uses `flag`, `statement` (its `libraries.toml`), installed with it.

`core` uses it, right after `values`. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `A0 each of them is A1` | Checks every item of the list A0 against A1; an error names the first item that fails. | `[1, 2, 3] each of them is > 1` |
| `one of A0 is A1` | True if an item of the list A0 equals A1; that item becomes "it". | `one of [11, 5] is 11` |
| `it should be converted to A0`<br>`it becomes A0` | Replaces "it" (found by `one of ... is ...`) in its list with A0. | `it should be converted to 1` |
