# statement

Statements: whole lines the reader knows. One file each, written in def with the words
of the `entry` library. `use core` uses them all.

| File | Use | Gives |
|---|---|---|
| `comment.def` | `use statement/comment` | `comment is X`: lines starting with `X` are comments, to the end of the file (each file starts with `//`) |
| `argument.def` | `use statement/argument` | `argument is X`: arguments are written `X0`, `X1`, …, to the end of the file (each file starts with `A`) |
| `indent.def` | `use statement/indent` | `indent N`: `N` spaces make one level, to the end of the file (each file starts with 4; a tab is one level) |
| `error.def` | `use statement/error` | `error MESSAGE`: stops the program with `MESSAGE` (`def-lang check` reads on) |
| `echo.def` | `use statement/echo` | `` `LINE` ``: prints `LINE`, then runs it; the line's value is its value |
| `scope.def` | `use statement/scope` | `in the scope of FILES`: where several files define the same phrase, the lines under it read the one of `FILES`; `in the scope of FILES, LINE`: so does the rest of its line |

```
statement comment
    words comment is A0
    does in def[written]
        set comment marker to A0

statement echo
    words ` A0 `
    does in def[written]
        show A0
        run A0
```

Two files with the same phrase: say which one a line means.

```
in the scope of web/http
    listen on host
    port is 8080

in the scope of io/audio, listen on dance
```

- `FILES` are named the way `use` names them: `web/http`, `helpers`; several with
  `and`: `web/http and io/audio`. A file that isn't used yet is used.
- A library's name is all its files: `in the scope of core`.
- With no scope, a line with a phrase two files define is an error: the interpreter
  doesn't guess.

**Writing your own:** [ENTRIES.md](../ENTRIES.md) says what each word of a statement means.
