# deflang-lib

Libraries for [def-lang](https://github.com/Pedram-A-Keyvani/deflang). The interpreter
knows only `python` and `use`; these libraries give the rest. Each library has one job,
and each of its files uses what it needs, so it works on its own.

## The entries

The interpreter knows only `python` and `use`; these declare the rest. The flags, statements and modifiers are written in def, with the words of `entry`.

| Library | Gives |
|---|---|
| [`language`](language/README.md) | Languages for definition bodies, one file each: def, html, css and javascript |
| [`flag`](flag/README.md) | Flags, written in brackets after a language, one file each: written and regex |
| [`statement`](statement/README.md) | Statements, whole lines the reader knows, one file each: comment, argument, indent, error and echo |
| [`modifier`](modifier/README.md) | Modifiers, words in front of a line, one file each: shared and internal |
| [`entry`](entry/README.md) | The words an entry's `does in def` is written with: set A0 to A1, upper-case, lower-case, stop with, show, run |

## Everyday words

`core` is a bundle: `use core` uses these libraries, in an order that matters (a library used earlier binds looser). A program may use only the ones it needs, in core's order.

| Library | Gives |
|---|---|
| [`core`](core/README.md) | A bundle of the everyday words of def-lang: values, questions, loops, lists, text, comparison, math and more, each a library of its own |
| [`loops`](loops/README.md) | Loops: repeat A0 times, for each A0 in A1, repeat while |
| [`questions`](questions/README.md) | Questions: A0 ?, is not ?, A0 that A1 |
| [`errors`](errors/README.md) | Errors: fail with A0, and A0, or if that fails, A1 |
| [`values`](values/README.md) | Values: A0 is A1, A0 if A1 otherwise A2, A0 means A1 |
| [`checks`](checks/README.md) | Checks of a list's items: A0 each of them is A1, one of A0 is A1, it becomes A0 |
| [`console`](console/README.md) | The console: say, give, wait |
| [`joined`](joined/README.md) | Text and values next to each other join into one text |
| [`logic`](logic/README.md) | Logic: either, both, not |
| [`comparison`](comparison/README.md) | Comparison: >, >=, <, <=, =, contains, is between, and their words |
| [`kinds`](kinds/README.md) | Kinds: is a whole number, is a number, is true or false |
| [`tables`](tables/README.md) | Tables: values under names |
| [`math`](math/README.md) | Math: + - * /, rounded, sum, average, squared, percent, and their words |
| [`text`](text/README.md) | Text: length, words, upper and lower case, starts with, split by, without ... at the end |
| [`lists`](lists/README.md) | Lists: count, first, last, largest, smallest, joined with, #, add, remove |
| [`formats`](formats/README.md) | Values written for others: as html, as json |
| [`time`](time/README.md) | Time: the time, today, and lines that run every so often |
| [`random`](random/README.md) | Chance: a random number, a random item |
| [`number-words`](number-words/README.md) | Numbers written in words: twenty one, one hundred and five |
| [`phrases`](phrases/README.md) | Phrases that read like English: the A0, their A0, all of A0 are A1, is A0 ?, A0 is empty |

## Files, settings, the program

For the programs that need them; not in `core`.

| Library | Gives |
|---|---|
| [`files`](files/README.md) | Files and folders, and lines that run when a file is saved |
| [`settings`](settings/README.md) | Settings: named values checked against the names and kinds a program takes |
| [`program`](program/README.md) | The program's own .def files: read the changed ones again |

## The web

Each layer is a library: the network (`http`), which address answers what (`server`), what is served (`website` for pages, `api` for data), HTML templates, and the browser side (`spa`). Where the server's settings come from is up to the program.

| Library | Gives |
|---|---|
| [`http`](http/README.md) | The network: listening on a host and a port, a request's path and query, and sending an answer |
| [`server`](server/README.md) | The server: which address answers what, and on which port |
| [`website`](website/README.md) | A website: pages for people, assets, and pages served under an address |
| [`api`](api/README.md) | An api: data for programs, as JSON |
| [`template`](template/README.md) | HTML templates: a file with {{ def-lang }} in it, filled in |
| [`spa`](spa/README.md) | The browser side of a single page application: views, forms that ask an api, fields the answers fill in |

**Writing your own:** [ENTRIES.md](ENTRIES.md) says what each word of a language, a
flag, a modifier and a statement means, with an example of each.

## Installing

In a program's folder:

```console
$ def-lang install https://github.com/Pedram-A-Keyvani/deflang-lib.git#core
$ def-lang install https://github.com/Pedram-A-Keyvani/deflang-lib.git#website --global
```

- The first copies `core` into the program's `libraries/`, with the libraries it uses.
- `--global` keeps the copies in the global folder instead, shared by every program.
- A library's `libraries.toml` lists the libraries it uses: they are installed with it.
  Installing `website` installs `server`, `http`, `core`, `files`, ... too.
- A program then uses a library by its name, or one of its files: `use core`,
  `use language/html`, `use website`.

## A library

A folder with a `library.toml` (`name`, and `version`) and its `.def` files: `use
NAME/FILE` runs one of them, and `use NAME` runs `main.def`, when there is one. A
`libraries.toml` lists the libraries it uses; a relative `from` is a folder of this
repository:

```toml
language = { from = "../language" }
```
