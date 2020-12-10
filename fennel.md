---
title: fennel
---

* some functions are built in lua and may not behave the same as fennel functions
  * i.e. (+ 1 2 3) is not a function call, so it will not work the same way when using it with unpack

# Destructuring

* Array
  * get first item and rest
```clojure
(let [[head & rest] [1 2 3 4]] (print head rest)) ;=> 1\n [2 3 4]
```
* table
  * you can use a short cut for single keys

```clojure
(let [{: a : b} {:a "x" :b "y"}] (print a)) ;=>  "x"
```

# varargs

When you need to make a variadic func, use varargs.

```clojure
(fn [...] (print ...))
```

but let's say you need to use those varargs in an enclosed function

```clojure
(fn [...] (fn [foo] (print foo ...)))
```

This will error because to the compiler, the varargs is a special var and always
refers to the enclosing function scope. To work around this you need to first
capture the value in the correct scope. Here we wrap the varargs in a
subsequentle table and assign it to a local variable.

Now when we call print, we will see a table is printed.

```clojure
(fn [...] (let [args [...]](fn [foo] (print foo ...)))
```

You may be asking why wrap it in a table? We do this because if we try to assign
it as just varargs, it will be treated like multi value returns, so only the
first argument would be captured.

Now, how to we spread that table in the call to print? We use unpack
(table.unpack in older versions of fennel)

```clojure
(fn [...] (let [args [...]](fn [foo] (print foo (unpack ...))))
```

This will now print the val of foo followed by the args passed to the wrapping
function
