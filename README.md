BuddyCron Profiles
==================

This repository contains questing profiles for **BuddyCron**, converted from the original
[BuddyWing](https://buddywing.net) collection. It is a curated collection, containing work from
various contributors.

Should you want to contribute your own profiles, please get in touch with one of the current contributors.

Layout
------

| Path             | What it is                                            |
|------------------|-------------------------------------------------------|
| `Questing/`      | **The profiles to run.**                              |
| `__Originals__/` | The original BuddyWing profiles, kept for reference.  |

All 182 profiles are present in `Questing/`, including the ones that needed no change. Nothing in
`__Originals__/` is modified.

Conversion
----------

`Questing/` was produced from `__Originals__/` by the changes below, and nothing else. Comments and
line endings are preserved, and no element is added, removed or reordered.

- **`X`/`Y`/`Z` collapsed into `XYZ`.** The separate-coordinate form is deprecated; both spellings
  mean the same position, so this is a tidy-up rather than a behaviour change. It was applied only
  to tags that actually carry a position.

- **Indentation aligned to nesting depth.** Alignment only — leading whitespace is the sole thing
  rewritten, and each file keeps its own style, so tab-indented profiles stay on tabs. Comment
  interiors and the continuation lines of a multi-line tag keep the layout the author gave them.

- **Quest-guard `<While>` blocks became `<If>`,** and their `UseObject`/`UseItem` children were
  given the matching `Step`/`Branch`/`Task`. A quest guard asks whether a step is still
  outstanding, which is a gate rather than a loop — and most of these profiles already wrote it
  that way. The attributes let each behaviour tell when it is finished instead of stopping after
  one attempt.

Known gaps
----------

- **60 `<While>` blocks remain.** Their conditions are area or level tests rather than quest
  guards, so the looping may be intentional. Worth a read-through.
- **13 children** already carried a `Step`/`Branch`/`Task` that disagreed with the guard around
  them. Those were left exactly as they were rather than being overwritten.
- **13 profiles are not well-formed XML** (mismatched tags, stray tokens). They were already that
  way in the originals and are worth fixing by hand.

Credits
-------
The following people have made noteworthy contributions to the profiles contained in this repository:

* Kickazz006
* Orlok Raven
