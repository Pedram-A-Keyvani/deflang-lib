# template

HTML templates: a file with `{{ def-lang }}` in it, each filled in with its value, escaped.

```
use template
```

It uses `core`, `files` (its `libraries.toml`), installed with it.

| Words | Does | Example |
|---|---|---|
| `template A0` | Reads an HTML file and fills in each `{{ ... }}` with the value of the def-lang inside it, HTML-escaped. | `template "pages/hi.html"` |
| `A0 with each {{ }} filled in` | The HTML text A0 with each {{ … }} filled in with the value of the def-lang inside it, escaped. The def-lang runs where this line runs. | `"<p>{{ 1 + 1 }}</p>" with each {{ }} filled in` |
