# language

Languages for definition bodies, one file each:

| File | Use | Gives |
|---|---|---|
| `html.def` | `use language/html` | `html …`: a def whose body is HTML |
| `css.def` | `use language/css` | `css …`: a def whose body is a style sheet |
| `javascript.def` | `use language/javascript` | `javascript …`: a def whose body is JavaScript for the browser |

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
