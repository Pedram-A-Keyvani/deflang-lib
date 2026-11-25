# math

Math: + - * /, rounded, sum, average, squared, percent, and their words.

```
use math
```

It uses `language`, `values` (its `libraries.toml`), installed with it.

`core` uses it, right after `tables`. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `A0 rounded to A1 places`<br>`A0 rounded to A1 place` | Rounds a number to A1 decimal places. | `22.857 rounded to 1 place` |
| `A0 rounded` | Rounds a number to the nearest whole number. | `2.6 rounded` |
| `A0 + A1` | Adds two numbers. | `2 plus 3` |
| `A0 - A1` | Subtracts A1 from A0. | `10 - 4` |
| `A0 / A1` | Divides A0 by A1. | `7 / 2` |
| `A0 * A1` | Multiplies two numbers. | `2 * 3` |
| `sum of A0` | Adds up the numbers in a list. | `sum of [1, 2, 3]` |
| `numbers from A0 to A1` | A list of the whole numbers from A0 to A1, counting down if A1 is smaller. | `numbers from 5 to 1` |
| `A0 squared` | A0 multiplied by itself. | `3 squared` |
| `half of A0` | A0 divided by 2. | `half of 9` |
| `A0 percent of A1` | A0 percent of A1. | `15 percent of 200` |
| `average of A0` | The average of the numbers in a list. | `average of [2, 4, 9]` |
