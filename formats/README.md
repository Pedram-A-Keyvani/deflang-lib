# formats

Values written for others to read: as HTML (escaped, so a browser shows it as text), as JSON.

```
use formats
```

`core` uses it, right after `lists`. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `A0 as html` | The text A0 as HTML shows it: <, >, & and quotes written so a browser shows them as text. | `"<b>" as html` |
| `A0 as json` | A0 as JSON: a table is an object, a list an array. | `[1, "a"] as json` |
