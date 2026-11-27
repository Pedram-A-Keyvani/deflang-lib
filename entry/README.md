# entry

The words an entry's `does in def` is written with: commands with no subject, acting on what the entry acts on (a flag on its definition, a modifier on the definition or the name after it, a language on the definition it runs, a statement on the file of its line). Their Python is here, so the entries can be def. The flags, statements and modifiers use it.

```
use entry
```

It uses `language`, `flag` (its `libraries.toml`), installed with it.

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
| `arguments` | a flag's or a modifier's definition | `as written` (it gets their words), `kept` (lines kept for later, each with its file), or `values` |
| `pattern` | a flag's or a modifier's definition | `regex` (a raw regular expression), or `readable` |
| `body` | a language's definition | a value, read as an expression: `upper-case` |
| `comment marker` | the file of a statement's line | the marker: `#` |
| `argument name` | the file of a statement's line | the name: `X` |
| `indent` | the file of a statement's line | a whole number: `2` |
| `scope` | the lines under a statement's line, and the rest of its `does` | files, or libraries: `web/http and io/audio`; where several files define the same phrase, theirs is read |

A modifier that needs more than a preset declares a `hook CYCLE PHASE in LANGUAGE`
instead of `does`; see [ENTRIES.md](../ENTRIES.md#9-cycle-hooks). Nothing is installed
until the modifier is written in front of a line.

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
