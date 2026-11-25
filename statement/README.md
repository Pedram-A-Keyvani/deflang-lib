# statement

Statements: whole lines the reader knows. One file each, written in def with the words
of `core/kernel.def`. `use core` uses them all.

| File | Use | Gives |
|---|---|---|
| `comment.def` | `use statement/comment` | `comment is X`: lines starting with `X` are comments, to the end of the file (each file starts with `//`) |
| `argument.def` | `use statement/argument` | `argument is X`: arguments are written `X0`, `X1`, …, to the end of the file (each file starts with `A`) |
| `indent.def` | `use statement/indent` | `indent N`: `N` spaces make one level, to the end of the file (each file starts with 4; a tab is one level) |
| `error.def` | `use statement/error` | `error MESSAGE`: stops the program with `MESSAGE` (`def-lang check` reads on) |
| `echo.def` | `use statement/echo` | `` `LINE` ``: prints `LINE`, then runs it; the line's value is its value |

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

**Writing your own:** [ENTRIES.md](../ENTRIES.md) says what each word of a statement means.
