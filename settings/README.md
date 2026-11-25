# settings

Settings: named values a program takes, checked against the names and kinds it takes. Wherever they come from: a file (files' `the table in file "settings.toml"`), memory, anywhere. The website sample's `def/running.def` takes them from settings.toml, and again whenever it is saved.

```
use settings
```

| Words | Does | Example |
|---|---|---|
| `A0 checked against A1` | The table A0, when each of its names is one of the table A1, and each value is of the kind A1 gives that name: "a whole number", "a number", "true or false" or "a text". Otherwise an error says which: a name it doesn't take, or a value of another kind. | `settings checked against kinds` |
