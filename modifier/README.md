# modifier

Modifiers: words in front of a line that change where something is seen. One file
each, written in def with the words of `core/kernel.def`:

| File | Use | Gives |
|---|---|---|
| `shared.def` | `use modifier/shared` | `shared NAME …`: one variable for the whole program |
| `internal.def` | `use modifier/internal` | `internal LANGUAGE …`: a definition only its own file sees |

`use core` uses both.

## shared

In front of a name: in this file, the name is the program's one shared variable. The
rest of the line runs as usual. Another file gets it with `use NAME from FILE`.

```
shared visits is 0
```

```
modifier shared
    does in def
        set name to shared
```

## internal

In front of a definition: only its own file sees it, its lines and its other
definitions (also when another file calls them).

```
internal python A0 halved
    return number(A0) / 2
```

```
modifier internal
    does in def
        set seen by to the file
```

**Writing your own:** [ENTRIES.md](../ENTRIES.md) says what each word of a modifier means.
