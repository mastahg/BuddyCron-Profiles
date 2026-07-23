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
  to tags that actually carry a position. `JumpTo` carries a second one for where the jump lands,
  so its `EndX`/`EndY`/`EndZ` became `EndXYZ` the same way.

- **Indentation aligned to nesting depth.** Alignment only — leading whitespace is the sole thing
  rewritten, and each file keeps its own style, so tab-indented profiles stay on tabs. Comment
  interiors and the continuation lines of a multi-line tag keep the layout the author gave them.

- **Object and item names renamed to the spelling the engine reads.** `UseObject` takes the
  object's name from `ObjectName` (or `OnObject`) and `UseItem` takes the item's from `ItemName`;
  neither reads the older `Name`, and `UseItem` no longer reads `Item` either. Left as they were,
  those tags named nothing and matched nothing. 4,139 `UseObject Name` → `ObjectName`, plus 245
  `UseItem Item` and 52 `UseItem Name` → `ItemName`. `UseItem`'s separate `OnObject` — what the
  item is used *on* — is untouched.

- **`UseTransport`'s `ToX`/`ToY`/`ToZ` removed.** The tag has one position, the transporter's own;
  where the ride ends is decided by `Option`, the entry it picks from the transporter's menu. There
  was never a destination to set, so unlike a rename there is nowhere for the values to go. 5,273
  attributes. Two are left: one tag spells its first coordinate `To=`, and the Nar Shaddaa profiles
  contain a stray triple with no opening tag at all. Both are worth a look.

- **Area checks in conditions repointed at the player.** Conditions that tested the zone through
  `BuddyTor.Client.AreaID` now read `Core.Player.AreaId`. The old name resolves to nothing, and one
  unresolvable name fails the whole condition rather than just its own term — so these gates were
  not merely testing the wrong thing, they were not running at all. 317 conditions.

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
  way in the originals and are worth fixing.
- **180 conditions still name something that does not exist**: `BuddyTor.Me.Companion.Name` in 9
  profiles and `BuddyTor.Client.AreaName` in 10. Like the area checks above, a condition written
  this way never runs. There is no drop-in replacement for either, so they need deciding one at a
  time.
- **A few coordinates are misspelled rather than deprecated** — a `JumpTo` whose first landing
  coordinate reads `End=`, and a `UseTransport` whose reads `To=`. Guessing at the intended
  attribute is not something the conversion will do.

Credits
-------
The following people have made noteworthy contributions to the profiles contained in this repository:

* Kickazz006
* Orlok Raven
