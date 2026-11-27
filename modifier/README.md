# modifier

Modifiers: words in front of a line that change where something is seen. `shared` and
`internal` are written with `define` hooks, not reserved `set` words, so they act only on
the line they are written in front of.

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
    hook define start in python
        NAME = self["entry"].get("name")
        HERE = self["file"]
        self["files"][HERE]["names"][NAME] = (HERE, NAME)
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
    hook define end in python
        DEFINITION = self["cycle"]["definition"]
        DEFINITION.visibility = "file"
        DEFINITION.seen_by = lambda file: file == DEFINITION.file
```

**Writing your own:** [ENTRIES.md](../ENTRIES.md#9-cycle-hooks) says what a hook sees, and
what the `set` words do.
