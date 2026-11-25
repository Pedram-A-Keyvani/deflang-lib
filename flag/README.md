# flag

Flags, written in brackets right after a language: `python[written] …`, several with
commas: `python[written, regex] …`. One file each, written in def with the words of
`core/kernel.def`. `use core` uses both.

| File | Use | Gives |
|---|---|---|
| `written.def` | `use flag/written` | `[written]`: the definition gets its arguments as they are written, not their values |
| `regex.def` | `use flag/regex` | `[regex]`: the pattern is a raw regular expression |
| `later.def` | `use flag/later` | `[later]`: the definition gets its arguments as lines to run later, each with the file it is written in |

## written

Use it when a definition needs the **words** of an argument: a name to store under, or
code to run later, many times, or maybe not at all.

```
python[written] A0 is A1
    self["variables"][A0] = self.run(A1)
```

```
flag written
    does in def
        set arguments to as written
```

## regex

` or ` splits alternatives, and `(A0: ...)` is an argument that matches only what is
after the colon.

```
python[regex] (A0: \d+)% or (A0: \d+) percent
    return number(A0) / 100
```

```
flag regex
    does in def
        set pattern to regex
```

## later

Use it when a definition keeps a line to run **later**, maybe many times: each
argument is the line as it is written, with the file it is written in, and
`the value of A0` runs it there, with variables of its own.

```
def[later] page A0 shows A1
    put A1 in pages at the value of A0
```

```
flag later
    does in def
        set arguments to kept
```

**Writing your own:** [ENTRIES.md](../ENTRIES.md) says what each word of a flag means.
