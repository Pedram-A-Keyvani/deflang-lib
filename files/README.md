# files

Files and folders of the program, and lines that run when a file is saved. A relative name starts in the program's folder.

```
use files
```

It uses `flag`, `time` (its `libraries.toml`), installed with it.

| Words | Does | Example |
|---|---|---|
| `the folder A0` | The folder A0; an error if there is none. | `the folder "static"` |
| `the file A0 in A1` | The file at the address A0 in one of the folders A1 (a folder, or a list of them): /style.css is FOLDER/style.css, and a folder is its index.html. Nothing if there is none, and never a file outside them. | `the file "/style.css" in folders` |
| `A0 is a file` | True if A0 is a file. | `"settings.toml" is a file` |
| `the time of file A0` | When the file A0 was last saved (a number that grows); nothing if there is no such file. | `the time of file "settings.toml"` |
| `the text of file A0` | The text in the file A0. | `the text of file "a.txt"` |
| `the bytes of file A0` | What the file A0 holds, as it is (bytes). | `the bytes of file "a.txt"` |
| `the kind of file A0` | The kind of the file A0, as the web names it: text/css, image/png, ... | `the kind of file "style.css"` |
| `the table in file A0` | The table in the TOML file A0. An error says the file's name, and what is wrong. | `the table in file "settings.toml"` |
| `when the file A0 is saved : A1` | Runs the line A1 whenever the file A0 is saved, while the program waits for something (it is looked at every second: time's `every … seconds`), with variables of its own, on top of those of the file of this line. | `when the file "settings.toml" is saved : say "saved"` |
