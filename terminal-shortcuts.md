---
title: terminal-shortcuts
---

---
title: Command Line Hax
links:
  - [what-does 2>&1 mean]:https://stackoverflow.com/questions/818255/in-the-shell-what-does-21-mean
tags:
  - command-line
  - bash
---

## Comand line hax

when running commands in a script, often you want the command to run without
outputting any results. Just run and be quite

```
File descriptor 1 is the standard output (stdout).
File descriptor 2 is the standard error (stderr).
```

ex: echo "foo" 2>&1

echo test > afile.txt

redirects stdout to afile.txt. This is the same as doing

echo test 1> afile.txt

To redirect stderr, you do:

echo test 2> afile.txt

`>&` is the syntax to redirect a stream to another file descriptor - 0 is stdin, 1 is stdout, and 2 is stderr.

You can redirect stdout to stderr by doing:

echo test 1>&2 # or echo test >&2

Or vice versa:

echo test 2>&1
