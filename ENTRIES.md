# Writing Languages, Flags, Modifiers and Statements

def-lang's interpreter knows two words: `python` and `use`. Everything else, like
`def`, `written`, `shared` or `comment is`, is an **entry**, declared in a `.def` file.
The libraries declare theirs, and you can declare your own the same way.

This page goes from the idea, to a first entry line by line, to each kind of entry.
The [reference](#7-reference) at the end lists every word.

1. [The Idea](#1-the-idea)
2. [Your First Entry](#2-your-first-entry)
3. [Languages](#3-languages)
4. [Flags](#4-flags)
5. [Modifiers](#5-modifiers)
6. [Statements](#6-statements)
7. [Reference](#7-reference)
8. [In Python](#8-in-python)

## 1. The Idea

There are four kinds of entry. The interpreter knows each one by where it stands in
a program, and runs its `does` at the right moment:

| Kind | You write it | It acts | On |
|---|---|---|---|
| **language** | at the start of a definition: `loud greeting for A0` | when that definition runs | the definition and its body |
| **flag** | in brackets after the language: `python[raw] …` | when the definition is made | the definition |
| **modifier** | in front of a line: `private def …`, `everywhere visits is 0` | right after the definition is made, or before the line runs | the definition, or the name |
| **statement** | as a whole line: `notes start with #` | when the line is read | the file of its line |

Every entry has the same shape:

```
// What it is: its help, shown on hover.
KIND NAME
    FIELD ...
    does in LANGUAGE
        BODY
```

## 2. Your First Entry

A flag that gives a definition the **words** of its arguments, not their values:

```
use core

// The definition gets its arguments' words, not their values.
flag raw
    does in def
        set arguments to as written

python[raw] the words of A0
    return A0

say the words of 1 + 2
```

```console
1 + 2
```

Line by line:

- `// The definition gets …` is its **help**: the editor shows it on hover.
- `flag raw` declares a **flag** named `raw`. A definition uses it in brackets:
  `python[raw] …`.
- `does in def` says what it does, written in **def**. Its body is one level deeper.
- `set arguments to as written` is that body: a command with no subject. It acts on
  what the flag acts on, the definition being made.
- `python[raw] the words of A0` is a definition with that flag. So `say the words of
  1 + 2` says `1 + 2`, not `3`.

The library's own `written` flag is exactly this entry.

## 3. Languages

A language runs the bodies of its definitions.

```
language NAME
    editor ID           (optional)
    does in LANGUAGE
        ...
```

```
use core

// Its body, in upper case.
language loud
    does in def
        set body to upper-case

loud greeting for A0
    hello A0, how are you?

say greeting for "sam"
```

```console
HELLO SAM, HOW ARE YOU?
```

- `loud greeting for A0` is a definition in the language `loud`.
- When it runs, `body` is its body with the values in: `hello sam, how are you?`.
  The definition's value is `body` when `does` ends.
- `set body to upper-case` changes it; `upper-case` and `lower-case` are words for it.
- `editor css` would color and format its bodies as CSS.
- Its definitions may have any flag: `loud[raw] …`.

## 4. Flags

A flag changes how one definition is made. It acts when the definition is made,
before its pattern is read.

```
flag NAME
    words PATTERN       (optional)
    does in LANGUAGE
        ...
```

A flag is written by its name, like `[raw]` in [section 2](#2-your-first-entry), or,
with `words`, by those words:

```
use core

// Says what a definition is for, when it is made.
flag for
    words for A0
    does in def[written]
        show A0

python[for doubling] twice A0
    return number(A0) * 2

say twice 4
```

```console
doubling
8
```

- `words for A0` writes the flag as `[for …]`. The words in the place of `A0` come to
  its `does`.
- `does in def[written]` gets them as they are written: `show A0` shows `doubling`.
  Without `[written]`, `A0` would be the text `"doubling"`, with its quotes.
- Several flags go in one pair of brackets: `python[raw, for doubling] …`.
- What a flag can change: `set arguments to …`, `set pattern to …`,
  `set seen by to …` ([reference](#7-reference)).

## 5. Modifiers

A modifier is a word in front of a line. In front of a definition, it acts on the
definition, right after it is made. In front of a name, it acts on the name, and then
the rest of the line runs.

```
modifier NAME
    does in LANGUAGE
        ...
```

**In front of a definition:** `helpers.def`

```
// Only its own file sees it.
modifier private
    does in def
        set seen by to the file

private def A0 halved
    A0 / 2

def A0 quartered
    half is A0 halved
    half halved
```

`main.def`, next to it:

```
use core
use helpers

say 8 quartered
say 8 halved
```

```console
2
unknown name '8 halved'
```

- `quartered` is in `helpers.def`, so it sees `halved`, also when `main.def` calls it.
- `main.def` doesn't see `halved`.

**In front of a name:** `counter.def`

```
// One variable for the whole program.
modifier everywhere
    does in def
        set name to shared

everywhere visits is 0
```

`main.def`, next to it:

```
use core
use visits from counter

visits is visits + 1
say visits
```

```console
1
```

- `everywhere visits is 0` makes `visits` a shared variable of `counter.def`, then runs
  `visits is 0`.
- `use visits from counter` gives `main.def` the same variable, not a copy.
- The library's `internal` and `shared` are these two entries.

## 6. Statements

A statement is a whole line the reader knows, by its words. Its words are matched
before anything else on a line, so they never read as part of an expression.

```
statement NAME
    words PATTERN
    does in LANGUAGE
        ...
```

```
use core

// Lines starting with A0 are comments, from here to the end of the file.
statement notes
    words notes start with A0
    does in def[written]
        set comment marker to A0

// Prints the line A0, then runs it: the line's value is its value.
statement loudly
    words loudly A0
    does in def[written]
        show A0
        run A0

notes start with #
# not run
loudly 2 + 3
```

```console
2 + 3
5
```

- `words notes start with A0` is the statement's line; the words in the place of `A0`
  come to its `does`.
- `does in def[written]` gets them as they are written: `#`, and `2 + 3`.
- `set comment marker to #` changes this file only: another file still starts with
  `//`.
- A statement whose `does` gives a value is like an expression line: `loudly 2 + 3`
  gives `5`.
- The library's `comment is`, `argument is`, `indent`, `error`, `` `LINE` `` and
  `in the scope of` are written this way.

## 7. Reference

### The reserved words

| Word | Means |
|---|---|
| `does in LANGUAGE[FLAGS]` | What the entry does, in that language (`def`, `python`, …); its body is one level deeper. It runs where the entry acts, in the variables of that line. Flags work as on a definition: `[written]` gets the arguments' words, not text. |
| `editor ID` | A language's: the editor's language for its bodies, for coloring and formatting them: `editor css`. |
| `flag NAME` | Declares a flag. |
| `language NAME` | Declares a language. |
| `modifier NAME` | Declares a modifier. |
| `replaces FILE` | This entry replaces the one of the same kind and name that `FILE` declared (see below). |
| `statement NAME` | Declares a statement. |
| `words PATTERN` | How a statement or a flag is written, like a pattern. Its `A0`, `A1`, … are the words in their places; its `does` gets them. A flag without `words` is just its name. |

The help of an entry is the comment lines right above it.

### `set … to …`

`set` takes both of its parts as they are written, and acts on what the entry acts on.

| `set …` | For | `to …` | Means |
|---|---|---|---|
| `arguments` | a flag, a modifier | `as written` | the definition gets its arguments' words, not their values |
| | | `values` | it gets their values (as at first) |
| `pattern` | a flag, a modifier | `regex` | the definition's pattern is a raw regular expression: ` or ` splits alternatives, `(A0: …)` is an argument |
| | | `readable` | it is read as words and arguments (as at first) |
| `seen by` | a flag, a modifier | `the file` | only the definition's own file sees it |
| | | `every file` | every file sees it (as at first) |
| `name` | a modifier, in front of a name | `shared` | the name is a shared variable of its file; another file gets it with `use NAME from FILE` |
| `body` | a language | a value | the definition's value: `upper-case`, `lower-case`, or any expression |
| `comment marker` | a statement | a marker | lines starting with it are comments, to the end of the file (each file starts with `//`) |
| `argument name` | a statement | a name | arguments are written with it and a number, to the end of the file (each file starts with `A`) |
| `indent` | a statement | a whole number | that many spaces make one level, to the end of the file (each file starts with 4) |
| `scope` | a statement | files or libraries, named the way `use` names them: `web/http and io/audio` | where several files define the same phrase, theirs is read: for the rest of the statement's `does`, and the lines under it |

If an entry can't set it, the error says what that entry can set. Outside an entry,
`set x to 2 + 3` sets the variable `x`.

### Other words

| Word | Means |
|---|---|
| `upper-case`, `lower-case` | a language's body, in upper or lower case |
| `stop with MESSAGE` | stops the program with `MESSAGE` (`def-lang check` reads on) |
| `show A0` | prints `A0`, while the program runs |
| `run A0` | runs `A0` as a line, where the entry acts, and gives its value |

### Replacing an entry

A program has one entry of each kind and name: two `language css` would be two ways
to read a `css …` definition. So declaring one another file declared is an error,
which catches a name you didn't mean to reuse. When you do mean it, say so with
`replaces`, naming the file the way `use` names it:

```
use core
use language/css

// CSS in lower case.
language css
    replaces language/css
    editor css
    does in def
        set body to lower-case

css look A0
    H1 { COLOR: A0; }

say look "RED"
```

```console
h1 { color: red; }
```

From `replaces` on, your entry is the one used, also by the definitions made before
it. The interpreter's own, `python` and `use`, can't be replaced.

## 8. In Python

`does in python` gets the same things through the kernel: what the entry acts on is
`self["entry"]` (`["definition"]`, `["name"]`, `["body"]`, `["values"]`, …), and a
statement's or a flag's words are `a[0]`, `a[1]`, …. The guide's
[5.1](https://github.com/Pedram-A-Keyvani/deflang#51-writing-an-entry) lists them all,
with the three hooks of a definition that `set` changes: `read_pattern`,
`read_argument` and `seen_by`.

```
flag raw
    does in python
        self["entry"]["definition"].read_argument = lambda text, read: text
```
