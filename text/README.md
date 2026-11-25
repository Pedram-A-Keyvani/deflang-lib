# text

Text: length, words, upper and lower case, starts with, split by, without ... at the end.

```
use text
```

`core` uses it, right after `math`. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `length of A0` | How many letters a text has. | `length of "hello"` |
| `words of A0` | Splits a text into a list of words. | `words of "a b c"` |
| `A0 in upper case` | The text in capital letters. | `"hi" in upper case` |
| `A0 in lower case` | The text in small letters. | `"HI" in lower case` |
| `A0 starts with A1` | True if the text A0 starts with A1. | `"/admin/users" starts with "/admin/"` |
| `A0 split by A1` | The parts of the text A0 between each A1, without the spaces around them. | `"visits, time" split by ","` |
| `A0 without A1 at the end` | The text A0 without A1 at its end, as often as it is there. | `"/admin//" without "/" at the end` |
