---
title: fennel
---

* some functions are built in lua and may not behave the same as fennel functions
  * i.e. (+ 1 2 3) is not a function call, so it will not work the same way when using it with unpack

# Destructuring

* Array
  * get first item and rest
```clojure
(let [[head & rest] [1 2 3 4]] (print head rest)) => ;1\n [2 3 4]
```
