# Sparrow

In [my previous post](https://github.com/elemel/blog/tree/master/2022/11/27)
from a few weeks ago, I described [Tabula](https://github.com/elemel/tabula),
an entity-component-system implementation in Lua. Tabula is archetype-based,
which means that rows having the same set of columns are stored together in a
table. These tables are called tablets in Tabula. If a column is added to a
row, or removed from it, the row automatically moves to another tablet that
matches the new set of columns. Tabula was mainly inspired by the articles by
[Sander Mertens](https://ajmmertens.medium.com/) on
[Flecs](https://github.com/SanderMertens/flecs).

Since then, I've explored another way of arranging data, namely sparse sets.
Here, my main inspiration has been the articles by
[Michele Caini](https://skypjack.github.io/) on
[EnTT](https://github.com/skypjack/entt). The new library is called
[Sparrow](https://github.com/elemel/sparrow). In comparison to Tabula,
Sparrow is more an in-memory database than a game engine. Overall, I'm happier
with how Sparrow has turned out, and may rewrite Tabula to bring it closer to
Sparrow.
