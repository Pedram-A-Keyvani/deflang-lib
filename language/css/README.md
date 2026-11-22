# css

`def css …`: a def whose body is a style sheet.

```
use css
```

- The body is the def's value, with `A0`, `A1`, … filled in as they are.
- A value with `{`, `}`, `;` or `<` in it is refused, so it can't break out of its
  rule, or out of the page's `<style>`.
- An HTML def puts it in with `<style def="name"></style>`; in a view, it only styles
  that view.

```
use core
use css
def css accent A0
    h1 { color: A0; }
say accent "teal"
```

```console
h1 { color: teal; }
```
