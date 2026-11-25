# kinds

What kind a value is: a whole number, a number, true or false. Not a text with one in it.

```
use kinds
```

`core` uses it, right after `comparison`. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `A0 is a whole number` | True if A0 is a whole number (not a text with one in it, nor true or false). | `8000 is a whole number` |
| `A0 is a number` | True if A0 is a number (not a text with one in it, nor true or false). | `0.5 is a number` |
| `A0 is true or false` | True if A0 is true or false. | `True is true or false` |
