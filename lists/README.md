# lists

A list's items: how many, the first, the last, the largest, the smallest, one by its place; joining them into one text; adding and removing them.

```
use lists
```

It uses `flag` (its `libraries.toml`), installed with it.

`core` uses it, right after `text`. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `count of A0` | How many items a list has. | `count of [3, 9, 2]` |
| `first of A0` | The first item of a list. | `first of [3, 9, 2]` |
| `last of A0` | The last item of a list. | `last of [3, 9, 2]` |
| `largest of A0` | The largest number in a list. | `largest of [3, 9, 2]` |
| `smallest of A0` | The smallest number in a list. | `smallest of [3, 9, 2]` |
| `A0 joined with A1` | The items of a list as one text, with A1 between them. | `["milk", "eggs"] joined with ", "` |
| `A0 # A1`<br>`A0 No. A1` | The item at position A1 of a list, counting from 1. | `[10, 20] # 2` |
| `add A0 to A1` | Adds A0 to the end of the list A1, making the list if needed. | `add "eggs" to list` |
| `remove A0 from A1` | Removes A0 from the list A1; an error if it isn't there. | `remove "milk" from list` |
