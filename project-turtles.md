---
title: Project Fractal Turtles
---

## Musings for project management

Why do we need visual differences between board/list/card. Are they really
different? Aren't they just containers for data?

Do they need constraints?

What are the different entities?
  * Project
  * Board
  * List
  * Card

Card can have lists. Are these the same as a List?

Cards belong to lists. Lists belong to Boards.

Projects are stand alone? Can they belong to boards?
* Yeah, like an Epic board.

So really, all the entities can just be connected together like nodes in a
graph. Some are edge nodes. Some are orphaned.

Cards can be containers of many projects. A Project can have a list of
associated cards or a list of Lists. Lists contain many Cards, but so can
Projects.

How is this visuallized. Part of the nice thing about kanban boards is that you
can get a overall feel of the state of a project by the progres and position of
cards.
