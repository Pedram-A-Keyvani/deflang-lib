# html

`def html …`: a def whose body is HTML.

```
use html
```

- The body is the def's value, with `A0`, `A1`, … filled in as escaped text.
- An element with `def="name"` and nothing inside gets that def's result as its
  content: `<nav def="site nav"></nav>`, `<script def="web script"></script>`,
  `<style def="hello style"></style>`.
- A result of `def html`, `def javascript` or `def css` goes in as it is (it is your
  own code); any other value is escaped.

```
use core
use html
def html greeting A0
    <p>Hello A0</p>
say greeting "<b>Sam</b>"
```

```console
<p>Hello &lt;b&gt;Sam&lt;/b&gt;</p>
```
