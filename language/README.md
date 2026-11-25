# language

Languages for definition bodies, one file each:

| File | Use | Gives |
|---|---|---|
| `def.def` | `use language/def` | `def …`: a definition whose body is def-lang |
| `html.def` | `use language/html` | `html …`: a def whose body is HTML |
| `css.def` | `use language/css` | `css …`: a def whose body is a style sheet |
| `javascript.def` | `use language/javascript` | `javascript …`: a def whose body is JavaScript for the browser |

## def

- The body's lines run one by one, like a file's lines, with `A0`, `A1`, … put in:
  their values written as code, or the words as they are written for a definition
  that keeps its arguments' words (`def[written]`).
- Its value is the value of the last line that has one.
- The variables it sets are its own and end with it. A `written` definition has none
  of its own: it runs where its words were written, with the variables there.
- Its definitions may have flags, like every language's: `def[written] …`.

```
use core
def A0 doubled
    A0 + A0
say 4 doubled
```

```console
8
```

## html

- The body is the def's value, with `A0`, `A1`, … filled in as escaped text.
- An element with `def="name"` and nothing inside gets that def's result as its
  content: `<nav def="site nav"></nav>`, `<script def="web script"></script>`,
  `<style def="hello style"></style>`.
- An `html`, `javascript` or `css` def's result goes in as it is (it is your own
  code); any other value is escaped.

```
use core
use language/html
html greeting A0
    <p>Hello A0</p>
say greeting "<b>Sam</b>"
```

```console
<p>Hello &lt;b&gt;Sam&lt;/b&gt;</p>
```

## css

- The body is the def's value, with `A0`, `A1`, … filled in as they are.
- A value with `{`, `}`, `;` or `<` in it is refused, so it can't break out of its
  rule, or out of the page's `<style>`.
- An HTML def puts it in with `<style def="name"></style>`; in a view, it only styles
  that view.

```
use core
use language/css
css accent A0
    h1 { color: A0; }
say accent "teal"
```

```console
h1 { color: teal; }
```

## javascript

- The body is the def's value, as code, with `A0`, `A1`, … filled in as JavaScript
  values (text is quoted, and can't end the page's `<script>` early).
- An HTML def puts it in with `<script def="name"></script>`.

```
use core
use language/javascript
javascript welcome A0
    alert(A0)
say welcome "Sam"
```

```console
alert("Sam")
```

**Writing your own:** [ENTRIES.md](../ENTRIES.md) says what each word of a language means.
