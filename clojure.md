---
title: clojure
---

## tooling

### linting

It's unfortunate that linting is not as great as js (through ts servers).
The problem is that clojure macros can be troublesome to evaluate by the
linters/lsps, so a lot of them require the user to define macro expansions

### Conjure

A lib for connecting vim to repl with added functionality to neovim client.

### clj-lsp

using this for completion as conjure is lacking a bit in this department. The
downside is this tool seems to do to much.

### leinigen

The current lead for project running/deps fetching

### boot

A gulp like task runner in contrast to Leinigen. Seems like a stale project.

### deps.edn

A tool built into clj to fetch deps. Still relatively new but receiving
adaptation even from other tooling

### shadow-clj

An npm tool that can be used in-lieu of the above but can be used in conj.
This tool is responsible for connecting a cljs project to the browser and
providing the repl access to the same. It's main concern is just cljs. It can
also manage npm packages.
