# tables

Tables: values under names.

```
use tables
```

`core` uses it, right after `kinds`. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `a new table` | A new table, with nothing in it. | `a new table` |
| `put A0 in A1 at A2` | Puts A0 in the table A1 under the name A2; what was there under that name goes. | `put value in pages at address` |
| `A0 at A1` | What the table A0 has under the name A1; nothing if it has none. | `pages at address` |
| `A0 has A1` | True if the table A0 has something under the name A1. | `pages has address` |
| `names of A0` | The names in the table A0, in the order they were put in. | `names of pages` |
| `A0 over A1` | The table A0, with the values of the table A1 where A0 has none. | `mine over defaults` |
