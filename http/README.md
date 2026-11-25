# http

The network, for any server: listening on a host and a port, a request's address and query, and sending an answer. It knows nothing of pages or apis: a line says what each request is answered with (the server library's: what the libraries that use it add).

```
use http
```

It uses `core` (its `libraries.toml`), installed with it.

| Words | Does | Example |
|---|---|---|
| `listen on A0 and A1, answering with A2` | Listens on the host A0 ("127.0.0.1": only this computer; "0.0.0.0": the computers on the network too) and the port A1 (0: a free one), and answers each request with the value of the line A2: an answer (`an answer with status …`). A2 runs for each request with variables of its own, on top of those of the file of this line; if it fails, or gives no answer, the request gets 500 and the message, as plain text. While it waits, and before each request, the lines time's `every … seconds` keeps run. It runs until Ctrl+C. | `listen on "127.0.0.1" and 8000, answering with "<p>hi</p>"` |
| `listen again on A0 and A1` | Listens on the host A0 and the port A1 instead, while it listens: the new one opens before the old one closes. If it can't, the old one stays, and it is an error that says why. | `listen again on "127.0.0.1" and 8001` |
| `an answer with status A0, kind A1 and content A2` | An answer to a request: its status (200, 404, ...), the kind of its content (text/html, application/json, ...), and the content, a text or bytes. | `an answer with status 404, kind "text/plain" and content "no"` |
| `the requested path` | The address the request asks for, like /hello; empty outside a request. | `the requested path` |
| `the query` | The request's query: `?name=Sam` in its address, and a form's fields, as a table. | `the query` |
| `the address it listens on` | Where it listens, as a browser opens it: http://localhost:8000. | `the address it listens on` |
| `it is listening` | True while it listens. | `it is listening` |
| `the host it listens on` | The host it listens on: "127.0.0.1", or "0.0.0.0". | `the host it listens on` |
| `the port it listens on` | The port it listens on. | `the port it listens on` |
