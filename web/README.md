# web

A web server for any website (`web/server`), and the script of a single page
application (`web/script`).

```
use web/server
use web/script
```

It uses the `core`, `language` and `flag` libraries (its `libraries.toml`), which
are installed with it.

```
use core
use language/html
use web/server
page "/" shows "<h1>Hello</h1>"
api "/api/sum" runs total is 1 + 2 and sends total
server on port 8000
start the server
```

`/` shows the page, `/api/sum` sends `{"total": 3}`, and it runs until Ctrl+C.

A page, an api or a `serve` line runs on every visit with variables of the visit's
own, on top of those of the file the line is in. So a file of routes sends the
shared variables it uses: `use visits from components/home`, then
`api "/api/visit" sends visits`.

## The server

`server.def`: the website, written in def. Its pages, apis and assets are tables; a
request is answered by small phrases, read inside one another: its api, its page, an
asset, the page served at its address or above it, or not found.

| Words | Does | Example |
|---|---|---|
| `server on port A0` | Sets the port of the website. Only this computer can connect. | `server on port 8000` |
| `server on port A0 for everyone` | Like `server on port`, but other computers on the network can connect too. | `server on port 8000 for everyone` |
| `page A0 shows A1` | Shows A1 at the address A0. A1 runs again on every visit. | `page "/hello" shows "<h1>Hi</h1>"` |
| `the assets are in A0`<br>`assets are in A0` | The website's assets (css, images, any file) are the files in the folder A0, sent as they are: /style.css is A0/style.css. The folder is relative to the program. | `the assets are in "files"` |
| `query A0` | The value of `?A0=...` in the address, or of a form field; empty if missing. On a page it is HTML-escaped, so visitors can't inject tags; an api sends it as data. | `query "name"` |
| `api A0 runs A1 and sends A2` | At the address A0, runs A1 and sends the values named in A2 (separated by commas) as JSON: variables A1 set, shared variables, or defs. Each request has its own variables, so one visitor's values never reach another. For a single page application. | `api "/api/sum" runs total is sum of [1, 2] and sends total` |
| `api A0 sends A1` | At the address A0, sends the values named in A1 (separated by commas) as JSON: defs (run for this request) or shared variables. | `api "/api/visits" sends visits` |
| `serve A0 at A1` | Shows A0 at the address A1 and every address under it (A1 "/" is /, /bmi, /hello, ...) that no api, page or asset answers and that has no file extension. A0 runs again on every visit. For a single page application, so its links and refreshes work; with several, the longest address wins. | `serve "<p>app</p>" at "/"` |
| `requested path` | The address of the page being visited, like /hello. | `requested path` |
| `template A0` | Reads an HTML file and fills in each `{{ ... }}` with the value of the def-lang inside it, HTML-escaped. | `template "pages/hi.html"` |
| `the settings are in A0` | Where the settings are, instead of settings.toml: a file, relative to the program ("": none). | `the settings are in "website.toml"` |
| `start the server` | Starts the website. It runs until Ctrl+C. How it runs comes from settings.toml in the program's folder, if there is one, and the file is read again whenever it is saved, while the website runs (see Settings). | `start the server` |

## The network

`http.def`: what def-lang can't do itself, in Python: listening on a port, a
request's address and query, and sending an answer. It knows nothing of pages or
apis: a line says what each request is answered with. `server.def` uses it, `in the
scope of http`.

| Words | Does | Example |
|---|---|---|
| `listen on A0 and A1, answering with A2` | Listens on the host A0 ("127.0.0.1": only this computer; "0.0.0.0": the computers on the network too) and the port A1 (0: a free one), and answers each request with the value of the line A2: an answer (`an answer with status …`), or a text, an HTML page. A2 runs for each request with variables of its own, on top of those of the file of this line; an error in it answers 500. Between requests, it runs the lines `every second while listening` keeps. It runs until Ctrl+C. | `listen on "127.0.0.1" and 8000, answering with "<p>hi</p>"` |
| `listen again on A0 and A1` | Listens on the host A0 and the port A1 instead, while it listens: the new one opens before the old one closes. If it can't, the old one stays, and it is an error that says why. | `listen again on "127.0.0.1" and 8001` |
| `every second while listening : A0` | Keeps the line A0, to run about once a second between requests while it listens, with variables of its own, on top of those of the file of this line. | `every second while listening : look at the settings again` |
| `an answer with status A0, kind A1 and content A2` | An answer to a request: its status (200, 404, ...), the kind of its content (text/html, application/json, ...), and the content, a text or bytes. | `an answer with status 404, kind "text/plain" and content "no"` |
| `the requested path` | The address the request asks for, like /hello; empty outside a request. | `the requested path` |
| `the query` | The request's query: `?name=Sam` in its address, and a form's fields, as a table. | `the query` |
| `the address it listens on` | Where it listens, as a browser opens it: http://localhost:8000. | `the address it listens on` |
| `the host it listens on` | The host it listens on: "127.0.0.1", or "0.0.0.0". | `the host it listens on` |
| `the port it listens on` | The port it listens on. | `the port it listens on` |

## Settings

`settings.toml` in the program's folder, if there is one (`the settings are in "x.toml"` names another). It is looked at every second
while the website runs, and read again whenever it is saved:

| Setting | Default | Is |
|---|---|---|
| `port` | `8000` | the port (it wins over `server on port`) |
| `everyone` | `false` | `true`: other computers on the network can connect |
| `watch` | `0` | seconds between looking for changed `.def` files, when a page is visited: a changed file's defs are read again. `0`: off (otherwise at least 0.1) |

## The script

`script.def`

| Words | Does | Example |
|---|---|---|
| `web script` | The script of a single page application. Put it in the page with <script def="web script"></script>, and each view in a <template>, like <template def="bmi view"></template>; the view for the address shows in the element that holds the templates. A view is <view path="/bmi" title="BMI calculator" loads="/api/x"> ... </view> (path="*" is any other address; loads asks an api when the view opens). It marks every link to the address with aria-current, sends a <form api="/api/x"> to that api, fills each {name} with the answer (as text, never as HTML) and opens the hidden element around it, keeps a view's <style def="name"></style> to that view, runs a view's <script def="name"></script> with `view` as the view's element (it hears an "answer" event with each answer), shows an error in the view's role="alert" element (or one it adds), and switches views without reloading when a link to "/..." is clicked or Back is pressed. | `serve site page at "/", with <script def="web script"></script> in html site page` |
