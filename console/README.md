# console

Talking with the person who runs the program: printing, asking, waiting. `give` with a condition checks each value with the checks library's `each of them is`.

```
use console
```

It uses `flag`, `checks` (its `libraries.toml`), installed with it.

`core` uses it, right after `checks`. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `give A0` | Asks the user for a value and stores it. With a number first, asks for that many and makes a list; a condition after the name checks each one. | `give 2 numbers less than or equal to 14` |
| `say A0` | Prints a value. | `say "Hello " "Sam"` |
| `wait A0 times`<br>`wait A0` | Waits until the user presses Enter A0 times. | `wait 2 times` |
