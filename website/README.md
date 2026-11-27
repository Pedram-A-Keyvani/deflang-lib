# website

A website: pages, for people. Each address shows a page; assets (css, images, any file) are sent as they are; a page can be served at an address and every address under it, for a single page application. A page that fails shows a 500 page with its message; an address nothing answers, a 404 page.

```
use website
```

It uses `core`, `flag`, `files`, `server` (its `libraries.toml`), installed with it.

```
use website
page "/" shows "<h1>Hello</h1>"
page "/about" shows about page          // a def, run on every visit
the assets are in "static"              // css, images, as they are
serve site page at "/"                  // "/" and every address under it
server on port 8000
start the server
```

| Words | Does | Example |
|---|---|---|
| `page A0 shows A1` | Shows A1 at the address A0. A1 runs again on every visit. | `page "/hello" shows "<h1>Hi</h1>"` |
| `the assets are in A0`<br>`assets are in A0` | The website's assets (css, images, any file) are the files in the folder A0, sent as they are: /style.css is A0/style.css. The folder is relative to the program. | `the assets are in "files"` |
| `the asset at A0 in A1` | The web asset at the address A0 in one of the folders A1: URL-decoded, with a leading / removed, and a folder served as its `index.html`. Nothing if there is none, and never a file outside them. | `the asset at "/style.css" in folders` |
| `serve A0 at A1` | Shows A0 at the address A1 and every address under it (A1 "/" is /, /bmi, /hello, ...) that no api, page or asset answers and that has no file extension. A0 runs again on every visit. For a single page application, so its links and refreshes work; with several, the longest address wins. | `serve "<p>app</p>" at "/"` |
