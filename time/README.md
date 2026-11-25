# time

The clock, and lines that run every so often while the program waits for something, like a server for requests.

```
use time
```

It uses `flag` (its `libraries.toml`), installed with it.

`core` uses it, right after `formats`. A library used earlier binds looser: on its own, use it in core's order ([core](../core/README.md)).

| Words | Does | Example |
|---|---|---|
| `time` | The current time, like 14:05. | `the time` |
| `today` | Today's date, like 2026-11-21. | `today` |
| `every A0 seconds : A1` | Runs the line A1 every A0 seconds while the program waits for something, like a server for requests, with variables of its own, on top of those of the file of this line. The same line again: its new interval; 0 seconds: no more. | `every 5 seconds : say "still here"` |
| `run what is due` | Runs the lines `every … seconds` keeps that are due. Something that waits says it often: a server, between requests. An error in one is said, and the others run. | `run what is due` |
