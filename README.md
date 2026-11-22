# deflang-lib

Libraries for [def-lang](https://github.com/Pedram-A-Keyvani/deflang). The interpreter
knows no words of its own; these libraries give them.

| Library | Folder | Gives |
|---|---|---|
| `core` | `core/` | values, questions, loops, lists, text, comparison, math |
| `html` | `language/html/` | `def html …`: bodies written in HTML |
| `css` | `language/css/` | `def css …`: style sheets |
| `javascript` | `language/javascript/` | `def javascript …`: code for the browser |
| `web` | `web/` | a web server, and the script of a single page application |

Each library's README lists its words.

## Installing

In a program's folder:

```console
$ def-lang install https://github.com/Pedram-A-Keyvani/deflang-lib.git#core
$ def-lang install https://github.com/Pedram-A-Keyvani/deflang-lib.git#web --global
```

- The first copies `core` into the program's `libraries/`.
- `--global` keeps the copy in the global folder instead, shared by every program.
- Installing `web` installs `javascript` too: `web/libraries.toml` lists it.
- A program then uses a library by its name: `use core`, `use html`,
  `use web/server`.

## A library

A folder with a `library.toml` (`name`, and `version`), its `.def` files, and
`main.def`, which `use NAME` runs. A `libraries.toml` lists the libraries it uses;
a relative `from` is a folder of this repository:

```toml
javascript = { from = "../language/javascript" }
```
