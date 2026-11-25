# core

A bundle of the everyday words: `use core` uses the libraries below, in this order. Each is a library of its own, with its own README; a program may use only the ones it needs.

```
use core
```

The order matters: a definition made earlier wraps the ones made later, so `x is 2 + 3 > 4` is `x is ((2 + 3) > 4)`. That is why the libraries go from the loosest words (loops, questions, `is`) to the tightest (math, text, lists).

First come the entries: the `def` language, `entry` (the words entries are written with), the flags, the statements and the modifiers. Then:

| Library | Gives |
|---|---|
| [`loops`](../loops/README.md) | Loops: repeat A0 times, for each A0 in A1, repeat while |
| [`questions`](../questions/README.md) | Questions: A0 ?, is not ?, A0 that A1 |
| [`errors`](../errors/README.md) | Errors: fail with A0, and A0, or if that fails, A1 |
| [`values`](../values/README.md) | Values: A0 is A1, A0 if A1 otherwise A2, A0 means A1 |
| [`checks`](../checks/README.md) | Checks of a list's items: A0 each of them is A1, one of A0 is A1, it becomes A0 |
| [`console`](../console/README.md) | The console: say, give, wait |
| [`joined`](../joined/README.md) | Text and values next to each other join into one text |
| [`logic`](../logic/README.md) | Logic: either, both, not |
| [`comparison`](../comparison/README.md) | Comparison: >, >=, <, <=, =, contains, is between, and their words |
| [`kinds`](../kinds/README.md) | Kinds: is a whole number, is a number, is true or false |
| [`tables`](../tables/README.md) | Tables: values under names |
| [`math`](../math/README.md) | Math: + - * /, rounded, sum, average, squared, percent, and their words |
| [`text`](../text/README.md) | Text: length, words, upper and lower case, starts with, split by, without ... at the end |
| [`lists`](../lists/README.md) | Lists: count, first, last, largest, smallest, joined with, #, add, remove |
| [`formats`](../formats/README.md) | Values written for others: as html, as json |
| [`time`](../time/README.md) | Time: the time, today, and lines that run every so often |
| [`random`](../random/README.md) | Chance: a random number, a random item |
| [`number-words`](../number-words/README.md) | Numbers written in words: twenty one, one hundred and five |
| [`phrases`](../phrases/README.md) | Phrases that read like English: the A0, their A0, all of A0 are A1, is A0 ?, A0 is empty |

Not in it, for the programs that need them: [`files`](../files/README.md), [`settings`](../settings/README.md), [`program`](../program/README.md), and the web libraries.

```
use core
numbers is [3, 9, 2]
say "largest: " largest of numbers
for each n in numbers: say n " squared is " n squared
average of numbers > 4 ?
    say "big on average"
is not ?
    say "small on average"
```

```console
largest: 9
3 squared is 9
9 squared is 81
2 squared is 4
big on average
```
