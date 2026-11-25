# server

The server: which address answers what, and on which port. What answers is up to the libraries that use it (website: pages; api: data) or the program; where its settings come from (a file, memory, anywhere) is up to the program. Each line it is given gives an answer for the request, or nothing when it isn't for it: `answer requests with` lines are asked first, in order; then `answer the other requests with` lines; then not found. A line that fails answers 500, with its message.

```
use server
```

It uses `core`, `flag`, `formats`, `http` (its `libraries.toml`), installed with it.

```
use server
server on port 8000                     // or from a file, memory, anywhere
answer requests with my answer          // first: an answer, or nothing
answer the other requests with mine     // when no line above answers
start the server                        // runs until Ctrl+C
```

`server on port` while it runs moves it there: the new port opens before the old one closes.

| Words | Does | Example |
|---|---|---|
| `server on port A0` | Sets the port of the server. Only this computer can connect. While it listens, it moves there: the new port opens before the old one closes. | `server on port 8000` |
| `server on port A0 for everyone` | Like `server on port`, but other computers on the network can connect too. | `server on port 8000 for everyone` |
| `answer requests with A0` | The requests a line answers: A0 gives an answer (`an answer with status …`), or nothing when the request isn't for it. Lines added earlier are asked first. | `answer requests with the page answer to the request` |
| `answer the other requests with A0` | Like `answer requests with`, for the requests none of those lines answers: assets, pages served under an address, ... | `answer the other requests with the asset answer to the request` |
| `start the server` | Starts the server. It runs until Ctrl+C. | `start the server` |
| `query A0` | The value of `?A0=...` in the address, or of a form field; empty if missing. For a page it is HTML-escaped, so visitors can't inject tags; for data, it is as it is. | `query "name"` |
| `the request is for data` | The request is for data, not a page: `query` gives its values as they are. An api says it before its line runs. | `the request is for data` |
| `requested path` | The address of the page being visited, like /hello. | `requested path` |
| `the address A0` | The address A0 without "/" at its end; "/" stays "/". | `the address "/admin/"` |
