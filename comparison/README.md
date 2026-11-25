# comparison

Comparison: >, >=, <, <=, =, contains, is between, and their words.

```
use comparison
```

It uses `language`, `values` (its `libraries.toml`), installed with it.

`core` uses it, right after `logic`. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `A0 >= A1` | True if the number A0 is greater than or equal to A1. | `3 greater than or equal to 3` |
| `A0 > A1` | True if the number A0 is greater than A1. | `5 > 3` |
| `A0 <= A1` | True if the number A0 is less than or equal to A1. | `4 <= 3` |
| `A0 < A1` | True if the number A0 is less than A1. | `2 is less than 3` |
| `A0 = A1` | True if A0 and A1 are equal: as numbers when both are numbers, otherwise as text. | `"Paris" = "Paris"` |
| `A0 contains A1` | True if the text A0 contains A1, or the list A0 has the item A1. | `"hello" contains "ell"` |
| `A0 is between A1 and A2`<br>`A0 between A1 and A2` | x is between 1 and 10  /  is x between 1 and 10? | `5 is between 1 and 10` |
