# api

An api: data, for programs, like the script of a single page application. Each request has its own variables, so one visitor's values never reach another; its `query` values come as they are, not escaped. An api that fails answers 400, with its message as JSON.

```
use api
```

It uses `core`, `flag`, `server` (its `libraries.toml`), installed with it.

```
use api
api "/api/sum" runs total is 1 + 2 and sends total
api "/api/visits" sends visits
server on port 8000
start the server
```

`/api/sum` answers `{"total": 3}`.

| Words | Does | Example |
|---|---|---|
| `api A0 runs A1 and sends A2` | At the address A0, runs A1 and sends the values named in A2 (separated by commas) as JSON: variables A1 set, shared variables, or defs. Each request has its own variables, so one visitor's values never reach another. For a single page application. | `api "/api/sum" runs total is sum of [1, 2] and sends total` |
| `api A0 sends A1` | At the address A0, sends the values named in A1 (separated by commas) as JSON: defs (run for this request) or shared variables. | `api "/api/visits" sends visits` |
