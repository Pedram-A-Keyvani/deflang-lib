# modifier

Modifiers: words in front of a line that change where something is seen. One file
each:

| File | Use | Gives |
|---|---|---|
| `shared.def` | `use modifier/shared` | `shared NAME …`: one variable for the whole program |
| `internal.def` | `use modifier/internal` | `internal LANGUAGE …`: a def only its own file sees |

`use core` uses both.

## shared

In front of a name: in this file, the name is the program's one shared variable. The
rest of the line runs as usual. Another file gets it with `use NAME from FILE`.

```
shared visits is 0
```

## internal

In front of a definition: only its own file sees it, its lines and its other defs
(also when another file calls them).

```
internal python A0 halved
    return number(A0) / 2
```
