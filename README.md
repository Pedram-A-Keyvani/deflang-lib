# deflang-lib

Libraries for [def-lang](https://github.com/Pedram-A-Keyvani/deflang). The interpreter
knows only `python` and `use`; these libraries give the rest.

| Library | Folder | Gives |
|---|---|---|
| `core` | `core/` | values, questions, loops, lists, text, comparison, math; and `kernel.def`, the words entries are written with |
| `language` | `language/` | `def …`, `html …`, `css …`, `javascript …`: bodies in those languages, one file each |
| `flag` | `flag/` | `written`, `regex`: flags, one file each |
| `statement` | `statement/` | `comment is`, `argument is`, `indent`, `error`, `` `…` ``: statements, one file each |
| `modifier` | `modifier/` | `shared`, `internal`: words in front of a line, one file each |
| `web` | `web/` | a web server, and the script of a single page application |

`use core` uses `language/def`, the flags, the statements and the modifiers first. The
flags, statements and modifiers are written in def, with the words of `core/kernel.def`.

**Writing your own:** [ENTRIES.md](ENTRIES.md) says what each word of a language, a
flag, a modifier and a statement means, with an example of each.

Each library's README lists its words.

## Installing

In a program's folder:

```console
$ def-lang install https://github.com/Pedram-A-Keyvani/deflang-lib.git#core
$ def-lang install https://github.com/Pedram-A-Keyvani/deflang-lib.git#web --global
```

- The first copies `core` into the program's `libraries/`.
- `--global` keeps the copy in the global folder instead, shared by every program.
- Installing `web` installs `language` too: `web/libraries.toml` lists it. In the
  same way, installing `core` installs `modifier`.
- A program then uses a library by its name, or one of its files: `use core`,
  `use language/html`, `use web/server`.

## A library

A folder with a `library.toml` (`name`, and `version`) and its `.def` files: `use
NAME/FILE` runs one of them, and `use NAME` runs `main.def`, when there is one. A
`libraries.toml` lists the libraries it uses; a relative `from` is a folder of this
repository:

```toml
language = { from = "../language" }
```
