---
description: Give your pets custom BlockBench models using ModelEngine, BetterModel, or ItemsAdder.
icon: palette
---

# Custom Pet Models

By default a MyPet pet looks like the vanilla mob it is — tame a wolf, you get a wolf. Custom pet models let your pets wear **custom BlockBench models** instead: a dragon, a mech, a fox-spirit, whatever your modelers can build — while still behaving like normal MyPet pets underneath.

{% hint style="info" %}
Every custom model rides on top of a real mob. That is why modeled pets still pathfind, fly, swim, take damage, sit, follow, level up, and use skills normally. The model is the costume; the pet is still a full MyPet pet. Nothing about leveling, the backpack, or skills changes.
{% endhint %}

## Requirements

You need exactly **one** of the following rendering plugins installed:

* **ModelEngine** — long-established standard, large model ecosystem (paid).
* **BetterModel** — free, open-source alternative. Requires a **Java 25** server.
* **ItemsAdder** — all-in-one content plugin with a built-in model engine (paid). Requires **ProtocolLib**.

**MythicMobs** is optional — only needed if you want players to tame MythicMob creatures in the world (Path C below).

If none of these are installed, MyPet behaves exactly as it does without this feature — everything is additive and provider-gated.

## Three ways to get a modeled pet

### Path A — Re-skin existing pets (easiest)

Add a `Model:` block to any pet type's section in `pet-config.yml` — for example, "every Wolf renders as `dragon`." From that point on, any wolf pet a player tames looks like a dragon. It is pure configuration: no per-pet setup, no special items, works the moment you save the file. Great for theme servers ("all cats are robot-cats") or giving a premium skin to an existing pet type.

See [pet-config.yml → Custom Pet Models](../configuration/pet-config.yml/README.md#custom-pet-models) for the `Model:` block syntax.

### Path B — Brand-new creatures

Define a creature that has no vanilla equivalent — a "Dragon" pet that, from the player's side, simply *is* a dragon. You choose how it moves (flying, walking, or swimming via the `Host:` field) and its health and stats. An admin gives one with `/petadmin create <player> mypet:<creature>` (custom creatures use the `mypet:` namespace; vanilla types use `minecraft:`), or players buy one from a [pet shop](../configuration/pet-shops.yml.md) if you list it there. Skills are granted through skilltrees, exactly like vanilla pet types.

See [pet-config.yml → Custom Pet Models](../configuration/pet-config.yml/README.md#custom-pet-models) for the custom creature syntax.

### Path C — Tame modeled creatures already in the world

If your server spawns modeled mobs in the world — a MythicMobs boss or an ItemsAdder creature — players can leash one into a pet using the same [leash requirement rules](leash-flags-requirements.md) MyPet already gives you. The creature keeps its model when it becomes a pet.

For this to work you define a custom creature whose **section name matches the source creature's id** and whose `Model:` block carries a **`Source:`** marker instead of a `Provider:`/`Id:`. That marker is what tells MyPet the model rides in from the tamed creature itself, so it is kept rather than stripped. See [pet-config.yml → Tameable modeled creatures](../configuration/pet-config.yml/README.md#tameable-modeled-creatures-source-driven) for the exact syntax (section name, `Host:`, and `Source:`).

When the player later releases it, **it turns back into the real creature**: release a tamed MythicMob and it becomes that wild MythicMob again — its own AI, abilities, drops, and model intact, not a bare vanilla animal.

To allow taming of MythicMob creatures, set `Disable-Leashing: false` in the `MythicMobs:` section of `hooks-config.yml`.

## The seven supported combinations

The three paths combine with the rendering/source plugins to give the seven ways a custom model can reach a pet. Each row is just a different `pet-config.yml` shape — pick the one that matches what you have.

| # | Way | Path | Who supplies the model | `pet-config.yml` shape |
| - | --- | ---- | ---------------------- | ---------------------- |
| 1 | Re-skin a pet with **ModelEngine** | A | ModelEngine renders MyPet's mob | `Model: { Provider: ModelEngine, Id }` on a vanilla type |
| 2 | Re-skin a pet with **BetterModel** | A | BetterModel renders MyPet's mob | `Model: { Provider: BetterModel, Id }` on a vanilla type |
| 3 | Custom creature rendered by **ModelEngine** | B | ModelEngine renders MyPet's host | `Host:` + `Model: { Provider: ModelEngine, Id }` |
| 4 | Custom creature rendered by **BetterModel** | B | BetterModel renders MyPet's host | `Host:` + `Model: { Provider: BetterModel, Id }` |
| 5 | Custom creature rendered by **ItemsAdder** | B | ItemsAdder renders MyPet's host | `Host:` + `Model: { Provider: ItemsAdder, Id }` |
| 6 | Tame a **MythicMobs** creature | C | MythicMobs (drawn by ModelEngine/BetterModel) | `Host:` + `Model: { Source }`, section name = MythicMob internal name |
| 7 | Tame / manage an **ItemsAdder** creature | C | ItemsAdder | `Host:` + `Model: { Source }`, section name = ItemsAdder entity id |

{% hint style="info" %}
Ways 1–5 are **rendered** (MyPet asks a provider to draw a model on its own mob); ways 6–7 are **source-driven** (the model rides in from a creature the player tames). They differ only in the `Model:` block — a `Provider:` + `Id:` for rendered, a `Source:` marker for source-driven. Re-skinning (Path A) also works with ItemsAdder if you prefer; ways 1 and 2 just show the two most common choices.
{% endhint %}

## Which provider gives you which features

|                              | ModelEngine | BetterModel | ItemsAdder | MythicMobs                     |
| ---------------------------- | ----------- | ----------- | ---------- | ------------------------------ |
| Draws custom models          | ✅           | ✅           | ✅          | — (uses ModelEngine/BetterModel) |
| Re-skin existing pets (A)    | ✅           | ✅           | ✅          | —                              |
| Brand-new creatures (B)      | ✅           | ✅           | ✅          | —                              |
| Tame modeled wild mobs (C)   | via mobs you spawn | via mobs you spawn | ✅ | ✅                    |

**ModelEngine, BetterModel, or ItemsAdder** powers the visual rendering (Paths A and B). **MythicMobs or ItemsAdder** is what enables taming creatures that spawn naturally in the world (Path C) — and MythicMobs is entirely optional; Paths A and B do not need it.

## What doesn't change

A modeled pet is still a MyPet pet in every way that matters: experience and leveling, the skill tree, sit/follow/aggression behavior, the backpack, naming, riding — all of it works as it does now. The custom model is purely visual.

## Configuration

All custom model settings live in [`pet-config.yml`](../configuration/pet-config.yml/README.md#custom-pet-models) under `MyPet.Pets`. Re-skinned types add a `Model:` block to their existing section; custom creatures add a new section with a `Host:` key plus `Model:`.

The only hooks-config.yml setting relevant to this feature is `MythicMobs.Disable-Leashing` (Path C) — see [hooks-config.yml](../configuration/hooks-config.yml.md#custom-pet-models).

Custom creatures (Path B) can be sold in a [pet shop](../configuration/pet-shops.yml.md) by listing the creature id in `pet-shops.yml` just like any other pet type.
