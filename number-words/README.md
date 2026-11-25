# number-words

Numbers written in words are numbers: `twenty one`, `one hundred and five`.

```
use number-words
```

It uses `flag` (its `libraries.toml`), installed with it.

`core` uses it, right after `random`. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `(A0: (?:(?:zero|one|two|three|four|five|six|seven|eight|nine|ten|eleven|twelve|thirteen|fourteen|fifteen|sixteen|seventeen|eighteen|nineteen|twenty|thirty|forty|fifty|sixty|seventy|eighty|ninety|hundred|thousand|million|billion)(?:\s+and\s+|-|\s+|$))+)` | numbers written in words: twenty one, one hundred and five, two thousand twenty six | `one hundred and five` |
