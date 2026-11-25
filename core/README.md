# core

The words most programs use: values, questions, loops, lists, text, comparison, math, tables and files.

```
use core
```

Each topic is one file, and `main.def` uses them in this order. The order matters:
a def made earlier wraps the ones made later, so `x is 2 + 3 > 4` is
`x is ((2 + 3) > 4)`. That is why the files go from the loosest words (loops,
questions, `is`) to the tightest (math, text).

It also uses the `modifier` library (its `libraries.toml`), installed with it, so
`use core` gives `shared` and `internal` too.

In the tables, `A0`, `A1`, … are what stands in their place on a line.

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

## Loops

`loops.def`

| Words | Does | Example |
|---|---|---|
| `repeat A0 times : A1` | Runs the line after the colon A0 times. | `repeat 3 times: say "hi"` |
| `for each A0 in A1 : A2` | Runs the line after the colon once for each item of the list A1, with the item in A0. | `for each n in [1, 2, 3]: say n * 2` |
| `repeat while A0 : A1` | Runs the line after the colon as long as A0 is true. Stops with an error after 100000 times. | `repeat while n < 5: n is n + 2` |

## Questions

`questions.def`

| Words | Does | Example |
|---|---|---|
| `is not ?` | Flips the answer of the last question, like an else. | `is not ?` |
| `A0 ?` | Asks a question: the indented lines below run only if A0 is true. | `5 > 3 ?` |
| `A0 that A1` | Puts the value of A0 in front of A1 and runs it. | `2 that > 1` |

## Values

`values.def`

| Words | Does | Example |
|---|---|---|
| `A0, or if that fails, A1` | Runs A0; if it stops with an error, runs A1 instead, with the error's message as `error`. | `say 1 / 0, or if that fails, say "can't"` |
| `A0 is A1` | Stores the value of A1 under the name A0. | `x is 2 + 3` |
| `A0 if A1 otherwise A2` | A0 when A1 is true, otherwise A2. Only the part that is chosen runs. | `175 / 100 if 175 > 3 otherwise 175` |
| `A0 means A1` | From now on, the words A0 are read as A1. | `tiny means 0.001` |
| `give A0` | Asks the user for a value and stores it. With a number first, asks for that many and makes a list; a condition after the name checks each one. | `give 2 numbers less than or equal to 14` |
| `fail with A0` | Stops the program with the message A0, a value like any other: "port " port " is taken". | `fail with "no " 1 + 1` |
| `the value of A0` | The value of the line A0, kept to run later (the flag `later`): run in the file it was written in, with variables of its own. Any other value is itself. | `the value of A0, for a line `1 + 2` kept for later` |
| `the values of A1 after A0` | Runs the kept line A0 ("": nothing) in the file the kept line A1 was written in, with variables of its own; then gives the values named in A1, separated by commas, from those variables: a table. | `the values of A1 after A0, for `total, count` after `total is 3`` |
| `say A0` | Prints a value. | `say "Hello " "Sam"` |
| `add A0 to A1` | Adds A0 to the end of the list A1, making the list if needed. | `add "eggs" to list` |
| `remove A0 from A1` | Removes A0 from the list A1; an error if it isn't there. | `remove "milk" from list` |
| `wait A0 times`<br>`wait A0` | Waits until the user presses Enter A0 times. | `wait 2 times` |

## Lists

`lists.def`

| Words | Does | Example |
|---|---|---|
| `A0 each of them is A1` | Checks every item of the list A0 against A1; an error names the first item that fails. | `[1, 2, 3] each of them is > 1` |
| `one of A0 is A1` | True if an item of the list A0 equals A1; that item becomes "it". | `one of [11, 5] is 11` |
| `it should be converted to A0`<br>`it becomes A0` | Replaces "it" (found by `one of ... is ...`) in its list with A0. | `it should be converted to 1` |

## Joined text

`joined.def`

| Words | Does | Example |
|---|---|---|
| `A0 "A1" A2`<br>`"A0" A1`<br>`A0 "A1"` | Text and values next to each other join into one text. | `"x = " 2` |

## Logic

`logic.def`

| Words | Does | Example |
|---|---|---|
| `either A0 or A1` | True if A0 or A1 is true. | `either 1 > 2 or 3 > 2` |
| `both A0 and A1` | True if A0 and A1 are both true. | `both 1 < 2 and 3 > 2` |
| `not A0` | The opposite of A0. | `not 1 > 2` |

## Comparison

`comparison.def`

| Words | Does | Example |
|---|---|---|
| `A0 >= A1` | True if the number A0 is greater than or equal to A1. | `3 greater than or equal to 3` |
| `A0 > A1` | True if the number A0 is greater than A1. | `5 > 3` |
| `A0 <= A1` | True if the number A0 is less than or equal to A1. | `4 <= 3` |
| `A0 < A1` | True if the number A0 is less than A1. | `2 is less than 3` |
| `A0 = A1` | True if A0 and A1 are equal: as numbers when both are numbers, otherwise as text. | `"Paris" = "Paris"` |
| `A0 is a whole number` | True if A0 is a whole number (not a text with one in it, nor true or false). | `8000 is a whole number` |
| `A0 is a number` | True if A0 is a number (not a text with one in it, nor true or false). | `0.5 is a number` |
| `A0 is true or false` | True if A0 is true or false. | `True is true or false` |
| `A0 contains A1` | True if the text A0 contains A1, or the list A0 has the item A1. | `"hello" contains "ell"` |
| `is greater than or equal to means >=`<br>`greater than or equal to means >=`<br>`is greater than means >`<br>`greater than means >`<br>`is less than or equal to means <=`<br>`less than or equal to means <=`<br>`is less than means <`<br>`less than means <`<br>`is equal to means =`<br>`equal to means =` | Words for the comparison symbols. Longer phrases are replaced first. | `5 greater than 3` |
| `A0 is between A1 and A2`<br>`A0 between A1 and A2` | x is between 1 and 10  /  is x between 1 and 10? | `5 is between 1 and 10` |

## Tables

`tables.def`

A table keeps values under names: any text, like a word or an address.

| Words | Does | Example |
|---|---|---|
| `a new table` | A new table, with nothing in it. | `a new table` |
| `put A0 in A1 at A2` | Puts A0 in the table A1 under the name A2; what was there under that name goes. | `put value in pages at address` |
| `A0 at A1` | What the table A0 has under the name A1; nothing if it has none. | `pages at address` |
| `A0 has A1` | True if the table A0 has something under the name A1. | `pages has address` |
| `names of A0` | The names in the table A0, in the order they were put in. | `names of pages` |
| `A0 over A1` | The table A0, with the values of the table A1 where A0 has none. | `mine over defaults` |

## Math

`math.def`

| Words | Does | Example |
|---|---|---|
| `A0 rounded to A1 places`<br>`A0 rounded to A1 place` | Rounds a number to A1 decimal places. | `22.857 rounded to 1 place`<br>`22.857 rounded to 2 places` |
| `A0 rounded` | Rounds a number to the nearest whole number. | `2.6 rounded` |
| `A0 + A1` | Adds two numbers. | `2 plus 3` |
| `A0 - A1` | Subtracts A1 from A0. | `10 - 4` |
| `A0 / A1` | Divides A0 by A1. | `7 / 2` |
| `A0 * A1` | Multiplies two numbers. | `2 * 3` |
| `A0 # A1`<br>`A0 No. A1` | The item at position A1 of a list, counting from 1. | `[10, 20] # 2` |
| `sum of A0` | Adds up the numbers in a list. | `sum of [1, 2, 3]` |
| `numbers from A0 to A1` | A list of the whole numbers from A0 to A1, counting down if A1 is smaller. | `numbers from 5 to 1` |
| `plus means +`<br>`minus means -`<br>`divided by means /`<br>`multiplied by means *` | Words for the math symbols. | `10 minus 4 divided by 2` |
| `A0 squared` | A0 multiplied by itself. | `3 squared` |
| `half of A0` | A0 divided by 2. | `half of 9` |
| `A0 percent of A1` | A0 percent of A1. | `15 percent of 200` |
| `average of A0` | The average of the numbers in a list. | `average of [2, 4, 9]` |

## Text and lists

`text.def`

| Words | Does | Example |
|---|---|---|
| `length of A0`<br>`count of A0` | How many letters a text has, or how many items a list has. | `length of "hello"` |
| `words of A0` | Splits a text into a list of words. | `words of "a b c"` |
| `A0 in upper case` | The text in capital letters. | `"hi" in upper case` |
| `A0 in lower case` | The text in small letters. | `"HI" in lower case` |
| `first of A0` | The first item of a list. | `first of [3, 9, 2]` |
| `last of A0` | The last item of a list. | `last of [3, 9, 2]` |
| `largest of A0` | The largest number in a list. | `largest of [3, 9, 2]` |
| `smallest of A0` | The smallest number in a list. | `smallest of [3, 9, 2]` |
| `A0 joined with A1` | The items of a list as one text, with A1 between them. | `["milk", "eggs"] joined with ", "` |
| `A0 as html` | The text A0 as HTML shows it: <, >, & and quotes written so a browser shows them as text. | `"<b>" as html` |
| `A0 as json` | A0 as JSON: a table is an object, a list an array. | `[1, "a"] as json` |
| `A0 starts with A1` | True if the text A0 starts with A1. | `"/admin/users" starts with "/admin/"` |
| `A0 split by A1` | The parts of the text A0 between each A1, without the spaces around them. | `"visits, time" split by ","` |
| `A0 without A1 at the end` | The text A0 without A1 at its end, as often as it is there. | `"/admin//" without "/" at the end` |

## Time and chance

`time.def`

| Words | Does | Example |
|---|---|---|
| `time` | The current time, like 14:05. | `the time` |
| `today` | Today's date, like 2026-11-21. | `today` |
| `random number between A0 and A1` | A random whole number from A0 to A1. | `random number between 1 and 6` |
| `random item of A0` | A random item of a list. | `random item of ["rock", "paper", "scissors"]` |

## Number words

`numbers.def`

| Words | Does | Example |
|---|---|---|
| `one, twenty one, one hundred and five, …` | numbers written in words: twenty one, one hundred and five, two thousand twenty six | `one hundred and five` |

## Files

`files.def`

A relative name starts in the program's folder.

| Words | Does | Example |
|---|---|---|
| `the folder A0` | The folder A0; an error if there is none. | `the folder "static"` |
| `the file A0 in A1` | The file at the address A0 in one of the folders A1 (a folder, or a list of them): /style.css is FOLDER/style.css, and a folder is its index.html. Nothing if there is none, and never a file outside them. | `the file "/style.css" in folders` |
| `A0 is a file` | True if A0 is a file. | `"settings.toml" is a file` |
| `the time of file A0` | When the file A0 was last saved (a number that grows); nothing if there is no such file. | `the time of file "settings.toml"` |
| `the text of file A0` | The text in the file A0. | `the text of file "a.txt"` |
| `the bytes of file A0` | What the file A0 holds, as it is (bytes). | `the bytes of file "a.txt"` |
| `the kind of file A0` | The kind of the file A0, as the web names it: text/css, image/png, ... | `the kind of file "style.css"` |
| `the table in file A0` | The table in the TOML file A0. An error says the file's name, and what is wrong. | `the table in file "settings.toml"` |
| `read the changed files again every A0 seconds` | Reads the program's .def files saved since they were read again, at most once every A0 seconds (0, or nothing: never): their definitions, in place of the old ones. Says which; a file with an error keeps its old definitions. | `read the changed files again every 5 seconds` |

## Phrases

`phrases.def`

| Words | Does | Example |
|---|---|---|
| `is A0 ?`<br>`are A0 ?`<br>`does A0 ?`<br>`do A0 ?` | Questions can also start with is, are, does or do:  is a > 5 ? | `is 5 > 3 ?` |
| `the A0` | "the numbers" is just "numbers" | `the numbers` |
| `their A0` | "their sum" is "sum of them" (them is the last list used) | `their sum` |
| `all of A0 are A1` | all of numbers are > 3 | `all of [1, 2] are > 1` |
| `print means say` | print is another word for say | `print "hi"` |
| `A0 is empty`<br>`A0 empty` | x is empty  /  is x empty? | `[] is empty` |

## Writing entries: `kernel.def`

[ENTRIES.md](../ENTRIES.md) explains these words one by one, with an example of each
kind of entry.

The words a `does in def` is written with: commands with no subject, acting on what the
entry acts on (a flag on its definition, a modifier on the definition or the name after
it, a language on the definition it runs, a statement on the file of its line). Their
Python is here, so the entries can be def.

| Word | For | Does |
|---|---|---|
| `set A0 to A1` | every kind | sets `A0` to `A1` on what the entry acts on; outside an entry's `does`, the variable `A0` |
| `upper-case`, `lower-case` | a language | the body in upper, or lower, case |
| `stop with A0` | a statement | stops the program with the message `A0` (`def-lang check` reads on) |
| `show A0` | a statement | prints `A0`, while the program runs |
| `run A0` | a statement | runs the line `A0` where the statement is, and gives its value |

What `set` sets (the words as they are written):

| `set …` | On | To |
|---|---|---|
| `arguments` | a flag's or a modifier's definition | `as written` (it gets their words), or `values` |
| `pattern` | a flag's or a modifier's definition | `regex` (a raw regular expression), or `readable` |
| `seen by` | a flag's or a modifier's definition | `the file` (only its own file sees it), or `every file` |
| `name` | a modifier's name | `shared`: a shared variable of its file |
| `body` | a language's definition | a value, read as an expression: `upper-case` |
| `comment marker` | the file of a statement's line | the marker: `#` |
| `argument name` | the file of a statement's line | the name: `X` |
| `indent` | the file of a statement's line | a whole number: `2` |
| `scope` | the lines under a statement's line, and the rest of its `does` | files, or libraries: `web/http and io/audio`; where several files define the same phrase, theirs is read |

```
// A flag of your own: the definition gets its arguments' words.
flag raw
    does in def
        set arguments to as written

// A language of your own: the body in capitals.
language loud
    does in def
        set body to upper-case
```

