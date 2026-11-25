# logic

Logic: either, both, not.

```
use logic
```

`core` uses it, right after `joined`. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `either A0 or A1` | True if A0 or A1 is true. | `either 1 > 2 or 3 > 2` |
| `both A0 and A1` | True if A0 and A1 are both true. | `both 1 < 2 and 3 > 2` |
| `not A0` | The opposite of A0. | `not 1 > 2` |
