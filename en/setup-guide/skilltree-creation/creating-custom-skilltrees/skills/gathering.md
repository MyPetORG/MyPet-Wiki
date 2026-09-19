---
description: Let your Pet gather resources — mining ore, felling trees, and fishing.
icon: pickaxe
---

# Gathering (Mining, Lumberjack & Fishing)

**Mining**, **Lumberjack**, and **Fishing** are three related skills that let a Pet gather resources on its own while it is out with you. They share the same rhythm: every few seconds the Pet looks for something to work on nearby, walks over to it, and plays the matching animation before producing the drop.

* **Mining** — breaks the nearest _exposed_ ore block (any face touching air) and drops its natural result, exactly as if you had mined it. Once it starts on a vein it clears the whole connected cluster before looking elsewhere.
* **Lumberjack** — fells the nearest tree from the bottom up. By default it takes **one log per work cycle**; the **Logs per cycle** upgrade lets it fell more of the trunk at once. Free-standing log pillars without leaves are left alone.
* **Fishing** — casts at nearby open water and, a moment later, drops vanilla fishing loot beside the Pet. No water is ever removed.

The Pet only works while it is spawned, its owner is online, and the owner is within **16 blocks**. It also commits to **one chore at a time** — you will see it walk to the ore or tree and break it before moving on to the next task, rather than doing everything at once. Once Lumberjack starts on a tree it stays on that tree until the whole trunk is down, and Mining likewise clears the entire connected ore vein it digs into before moving on (unless you walk away and it follows you).

Each of these skills can be switched on or off per pet from the **pet menu** (`/pet`) — handy for pausing the auto-gathering without changing the skilltree.

### Tools <a href="#tools" id="tools"></a>

By default each skill needs a real tool in the Pet's [Backpack](backpack.md):

| Skill      | Required tool  |
| ---------- | -------------- |
| Mining     | a pickaxe      |
| Lumberjack | an axe         |
| Fishing    | a fishing rod  |

The tool has to actually be able to harvest the target — a wooden pickaxe will **not** mine diamond ore, for example. The Pet uses the real tool from its backpack, so its **enchantments apply** (Fortune and Silk Touch change the drops) and it **loses durability** with each use, breaking and disappearing when it is worn out. When the Pet has no usable tool it simply does nothing and reminds the owner to restock.

Because tools and drops both live in the backpack, these skills pair naturally with [Backpack](backpack.md) and [Pickup](pickup.md): give the Pet all three and it will hold its own tools and collect everything it gathers.

Grant the **No tool required** upgrade (`toolless`) to remove the tool requirement entirely — the Pet then works bare-pawed with no durability cost. This makes a good high-level reward on a gathering skilltree.

### Settings <a href="#settings" id="settings"></a>

Each of the three skills is configured the same way through the [skilltree](../../what-are-skilltrees.md) skill settings:

| Setting              | Key        | Type    | Meaning                                                                 |
| -------------------- | ---------- | ------- | ----------------------------------------------------------------------- |
| Range                | `range`    | number  | How far (in blocks) the Pet searches for work. Capped at 8 blocks.      |
| Interval             | `interval` | integer | Seconds between attempts. Both Range and Interval must be above 0.      |
| No tool required     | `toolless` | boolean | When `true`, the Pet works without a tool (no durability). Default `false`. |

**Lumberjack** has one extra setting:

| Setting        | Key    | Type    | Meaning                                                                      |
| -------------- | ------ | ------- | ---------------------------------------------------------------------------- |
| Logs per cycle | `logs` | integer | Trunk logs felled each cycle. Base is 1; add to it to fell more at once.      |

Example skilltree entry that grants Mining at level 1 (tool required) and removes the tool requirement at level 5:

```json
"Mining": {
  "Upgrades": {
    "1": { "Range": "+6", "Interval": "+2" },
    "5": { "toolless": true }
  }
}
```

Lumberjack and Fishing use the exact same keys.

### Disabling globally <a href="#disabling-globally" id="disabling-globally"></a>

Each skill has a server-wide kill-switch in [`config.yml`](../../../getting-started/configuration/config.yml.md) — `MyPet.Skill.Mining.Active`, `MyPet.Skill.Lumberjack.Active`, and `MyPet.Skill.Fishing.Active` (all `true` by default). Setting one to `false` leaves the skill visible in skilltrees but stops it from doing any work.
