---
title: out-of-the-tarpis
---

# Out of the tar pits

## 1:

Complexity is the single most major difficulty in successful software
develepment

* The major contributor to complexity is
  * handling state and the burden it adds to trying to analyse a system
  * code volume
  * flow of control


## 2: Complexity

* is the root cause of a vast majority of software
* Complexity destroys understanding.
* being able to think and reason about a system is crucial to performance
* complexity has a way of compounding difficulty
* The price of reliability is the persuit of of the utmost simplicity


> I conlude that there are two ways of constructing a software design: One way
> is to make it so simple that there are obviously no deficiencies adn that the
> other way is to make it so complicated that there are no obvious deficiencies.
> The first method is far more difficult.
>> - C. A. R. Hoare (1980)

* creating and maintaining such systems causes us to expend huge resources


## 3: Approaches to Understanding

* testing: attempting to understand a system from the outside
* informal reasoning: attempting to understand the system from the inside
* A key problem of testing
  * it doesn't tell you anything about the behavior system when a diff set of
    inputs is used
  * "have we perfomed the right tests?"


> Testing is hopelessly inadequate...(it) can be used very effectively to show
> the presence of bugsbut never to show their absense.
>> - Edsger W. Dijkstra (1971)

* Rely on testing at your peril.

> Invest in simplicity

## 4: Causes of Complexity

* due to state
  * impacts on tests
    * one particular state does not tell you anything about the behavior of a
      system in another state

* impact of state on informal reasoning
  * increasing the number of state makes mental simulations increasingly difficult

*The Problem with state*

> When you let the nose of a camel into the tent, the rest of him tends to follow

### Caused by Control

> Controll is basically about the order in which things happen.

> They are being forced to specify an aspect of *how* the system should work
> rather than simply *what* is desired.

* Imperative vs Declarative

### Other Causes

* dead code
* duplicate code
* unnecessary abstraction (data abstraction)
* missed abstraction
* poor modularization
* poor documentation


* *Complexity breads Complexity*
* *Simplicity is **HARD** *
* *Power Corrupts*

# 5: Classical Approaches to Managing Complexity

* Object Oriented
  * State encapsulation
  * Object Identity aka *Intensional Identity*
  * in contrast to *Extensional Identity* (objects with the same shape)
  * *suffers from all the problems of managing state above
  * does not provide an adequate foundation for avoiding complexity

* Functional
  * avoids state
  * gains referential transparency


* Kinds of state
  * when we talk about state we are really talking about mutable state


* state and modularity

> The trade of is between complexity (with the ability to take a shortcut when
> making some specific types of change) and simplicity (with huge improvements in
> both testing and reasoning)

> Problems arise when the system to be built must maintain state of some kind


