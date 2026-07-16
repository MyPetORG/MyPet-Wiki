---
description: >-
  Give your pets custom BlockBench models using ModelEngine, BetterModel, or
  ItemsAdder.
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

**MythicMobs** is optional — only needed for Path C, **Custom Creature — MythicMobs** (spawning/adopting real MythicMob creatures).

If none of these are installed, MyPet behaves exactly as it does without this feature — everything is additive and provider-gated.

## Three ways to get a modeled pet

### Path A — Re-skin existing pets (easiest)

Add a `Model:` block to any pet type's section in `pet-config.yml` — for example, "every Wolf renders as `dragon`." From that point on, any wolf pet a player tames looks like a dragon. It is pure configuration: no per-pet setup, no special items, works the moment you save the file. Great for theme servers ("all cats are robot-cats") or giving a premium skin to an existing pet type.

See [pet-config.yml → Custom Pet Models](../configuration/pet-config.yml/#custom-pet-models) for the `Model:` block syntax.

### Path B — Brand-new creatures

Define a creature that has no vanilla equivalent — a "Dragon" pet that, from the player's side, simply _is_ a dragon. You choose how it moves (flying, walking, or swimming via the `Host:` field) and its health and stats. Players get one three ways — because **the model is the identity**, any mob wearing the creature's model is that creature:

* An admin runs `/petadmin create <player> mypet:<creature>` (custom creatures use the `mypet:` namespace; vanilla types use `minecraft:`).
* A player buys one from a [pet shop](../configuration/pet-shops.yml.md), if you list it there.
* A player **leashes any mob wearing that model** — one you `/meg summon` / `/bm spawn` into the world, or one MyPet left behind when a pet of this type was released — using the normal [leash requirement rules](leash-flags-requirements.md).

Releasing a custom creature leaves a wild mob still wearing its model, so it can be re-leashed back into the same pet. See [pet-config.yml → Custom Pet Models](../configuration/pet-config.yml/#custom-pet-models) for the syntax.

### Path C — Custom Creature — MythicMobs

MythicMobs is a **fourth custom-creature provider** — same shape as ModelEngine/BetterModel/ItemsAdder, just spawned differently: instead of MyPet drawing a model on a vanilla host, MyPet spawns (or adopts) the **real MythicMob**, model and all. Define a custom creature with `Model: { Provider: MythicMobs, Id: <mythicmob-internal-name> }` — the section name is arbitrary, exactly like the other three providers; the mob's identity lives in `Id:`. See [pet-config.yml → Custom creature definitions](../configuration/pet-config.yml/#custom-creature-definitions-host).

Players get one the same three ways as any custom creature:

* An admin runs `/petadmin create <player> mypet:<creature>` — MyPet spawns the actual MythicMob and adopts it as the pet.
* A player buys one from a [pet shop](../configuration/pet-shops.yml.md) — same result.
* A player **leashes a wild MythicMob** with the matching internal name — using the normal [leash requirement rules](leash-flags-requirements.md).

When the player later releases it, **it turns back into the real MythicMob** — its own AI, abilities, drops, and model intact, not a bare vanilla animal.

To allow taming, set `Disable-Leashing: false` in the `MythicMobs:` section of `hooks-config.yml`.

## The six methods

Each row is a different `pet-config.yml` shape — pick the one that matches what you have.

| # | Method                             | Config shape                                             | Obtained by                                                           |
| - | ---------------------------------- | -------------------------------------------------------- | --------------------------------------------------------------------- |
| 1 | Re-skin a pet with **ModelEngine** | `Model: { Provider: ModelEngine, Id }` on a vanilla type | taming that vanilla mob                                               |
| 2 | Re-skin a pet with **BetterModel** | `Model: { Provider: BetterModel, Id }` on a vanilla type | taming that vanilla mob                                               |
| 3 | Custom creature — **ModelEngine**  | `Host:` + `Model: { Provider: ModelEngine, Id }`         | `/petadmin create`, pet shop, **or** leashing a mob wearing its model |
| 4 | Custom creature — **BetterModel**  | `Host:` + `Model: { Provider: BetterModel, Id }`         | create / pet shop / leash a mob wearing its model                     |
| 5 | Custom creature — **ItemsAdder**   | `Host:` + `Model: { Provider: ItemsAdder, Id }`          | create / pet shop / leash a mob wearing its model                     |
| 6 | Custom creature — **MythicMobs**   | `Host:` + `Model: { Provider: MythicMobs, Id }`          | `/petadmin create` / pet shop / leashing the MythicMob                |

{% hint style="info" %}
Every method now carries a `Model.Id`, so **`Model.Id` is not the discriminator** between rendered and source-driven. That split is decided by the **provider's plugin type**: ModelEngine/BetterModel/ItemsAdder are renderers (MyPet draws the model on its host), MythicMobs is source-only (MyPet spawns/adopts the real creature and its model rides along). Method 6 is the **only source-driven** one, because MyPet can't draw a MythicMob's model itself — release respawns the real MythicMob.
{% endhint %}

## Which provider gives you which features

|                                     | ModelEngine         | BetterModel         | ItemsAdder          | MythicMobs                       |
| ----------------------------------- | ------------------- | ------------------- | ------------------- | -------------------------------- |
| Draws custom models                 | ✅                   | ✅                   | ✅                   | — (uses ModelEngine/BetterModel) |
| Re-skin existing pets (A)           | ✅                   | ✅                   | ✅                   | —                                |
| Brand-new / adopted creatures (B/C) | ✅ (rendered)        | ✅ (rendered)        | ✅ (rendered)        | ✅ (source-driven)                |
| Create / leash → its pet            | ✅ (custom creature) | ✅ (custom creature) | ✅ (custom creature) | ✅ (custom creature)              |

**ModelEngine, BetterModel, or ItemsAdder** power the visual rendering; **MythicMobs** is an optional layer.

## Animations

Across all six methods, MyPet plays a handful of **animations** on the model automatically — on spawn, despawn, sit/unsit, and attack. If your models name those animations the MyPet defaults (`spawn`, `despawn`, `sit`, `sit_loop`, `unsit`, `attack`) they work out of the box; otherwise you can remap the names per pet type. Walking, idling, and other movement animations are handled by the rendering plugin itself, not by MyPet. See [pet-config.yml → Model animations](../configuration/pet-config.yml/#model-animations) for the full list and how to override names.

## What doesn't change

A modeled pet is still a MyPet pet in every way that matters: experience and leveling, the skill tree, sit/follow/aggression behavior, the backpack, naming, riding — all of it works as it does now. The custom model is purely visual.

## Configuration

All custom model settings live in [`pet-config.yml`](../configuration/pet-config.yml/#custom-pet-models) under `MyPet.Pets`. Re-skinned types add a `Model:` block to their existing section; custom creatures add a new section with a `Host:` key plus `Model:`.

The only hooks-config.yml setting relevant to this feature is `MythicMobs.Disable-Leashing` (Path C) — see [hooks-config.yml](../configuration/hooks-config.yml.md#custom-pet-models).

Custom creatures — Path B (rendered) and Path C (MythicMobs) alike — can be sold in a [pet shop](../configuration/pet-shops.yml.md) by listing the creature id in `pet-shops.yml` just like any other pet type.
