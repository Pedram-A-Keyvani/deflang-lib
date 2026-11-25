# phrases

Phrases that make lines read like English: `the numbers`, `their sum`, `all of numbers are > 3`, `is x empty ?`.

```
use phrases
```

It uses `language`, `flag`, `questions`, `checks`, `values`, `console`, `comparison`, `lists` (its `libraries.toml`), installed with it.

`core` uses it, right after `number-words`. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `is A0 ?`<br>`are A0 ?`<br>`does A0 ?`<br>`do A0 ?` | Questions can also start with is, are, does or do:  is a > 5 ? | `is 5 > 3 ?` |
| `the A0` | "the numbers" is just "numbers" | `the numbers` |
| `their A0` | "their sum" is "sum of them" (them is the last list used) | `their sum` |
| `all of A0 are A1` | all of numbers are > 3 | `all of [1, 2] are > 1` |
| `A0 is empty`<br>`A0 empty` | x is empty  /  is x empty? | `[] is empty` |
