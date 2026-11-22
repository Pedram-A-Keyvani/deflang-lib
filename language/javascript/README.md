# javascript

`def javascript …`: a def whose body is JavaScript for the browser.

```
use javascript
```

- The body is the def's value, as code, with `A0`, `A1`, … filled in as JavaScript
  values (text is quoted, and can't end the page's `<script>` early).
- An HTML def puts it in with `<script def="name"></script>`.

```
use core
use javascript
def javascript welcome A0
    alert(A0)
say welcome "Sam"
```

```console
alert("Sam")
```
