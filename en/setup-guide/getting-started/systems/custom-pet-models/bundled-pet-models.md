---
description: >-
  How to add the Capybara and the Chameleon — the two custom-model creatures
  that ship inside the MyPet jar.
icon: otter
---

# Bundled Models — Capybara & Chameleon

MyPet 4 ships two ready-made BlockBench models inside the plugin jar: **`capybara`** and **`chameleon`** (made by [HeavenCreations](https://builtbybit.com/creators/heavencreations.326565/)).

{% hint style="warning" %}
**They are not pet types out of the box.** MyPet bundles the **models**, not finished creatures. There is no `Capybara` pet type until **you** define one in `pet-config.yml` — so `/petadmin create <player> mypet:capybara` will not work on a fresh install, and the Capybara does not appear in `/petshop` or in tab-completion.

Defining it takes about two minutes and is described below. Once you do, MyPet copies the bundled `.bbmodel` into your model plugin automatically — you never download or install a model file yourself.
{% endhint %}

## Before you start

You need **BetterModel** or **ModelEngine** installed. Those are the only two providers the bundled installer can write into:

| Provider        | Bundled Capybara/Chameleon?                                   | Where MyPet installs the file                     |
| --------------- | ------------------------------------------------------------- | ------------------------------------------------- |
| **BetterModel** | ✅ Yes (free; needs a Java 25 server)                          | `plugins/BetterModel/models/capybara.bbmodel`     |
| **ModelEngine** | ✅ Yes (paid)                                                  | `plugins/ModelEngine/blueprints/capybara.bbmodel` |
| ItemsAdder      | ❌ No — ItemsAdder models are content packs, not drop-in files | —                                                 |
| MythicMobs      | ❌ No — MythicMobs is source-driven, it supplies its own mobs  | —                                                 |

## Add the Capybara

{% hint style="success" %}
**Name the section exactly `Capybara`** (and `Chameleon` for the other). MyPet's bundled skilltrees list those names in their eligible mob types — a Capybara named `Capy` or `MyCapybara` gets **no** default skilltrees. See [Which skilltrees they get](bundled-pet-models.md#which-skilltrees-they-get).
{% endhint %}

### Option A — the web editor (recommended)

1. Run `/mypet editor` in-game and open the link.
2. Go to **pet-config** and click **Create custom pet**.
3. Pick **BetterModel** (or **ModelEngine**).
4. On the model card, leave the **MyPet default** tab selected and choose **capybara**.
5. Name the creature `Capybara`, pick a **host mob** (see [`Host:`](bundled-pet-models.md#choosing-a-host) — `Pig` is a good default), set HP/Speed, then **Create**.
6. Click **`Review & Save`** at the bottom of the sidebar, check the `pet-config.yml` entry in the change list, then **`Apply Changes`**.

The wizard only edits the copy in your browser — nothing reaches the server until you apply. **`Apply Changes` reloads the server for you**: it writes `pet-config.yml`, registers `Capybara` as a pet type with its permission nodes, and installs the bundled model. No `/mypet reload config`, no restart. See [Saving Changes](../../../configurator/configurator/saving-changes.md).

### Option B — edit `pet-config.yml` by hand

Add this section under `MyPet.Pets`:

{% code title="pet-config.yml" %}
```yaml
MyPet:
  Pets:
    Capybara:
      Host: Pig                 # movement profile — a walking land animal
      HP: 20.0
      Speed: 0.3
      LeashItem: lead
      Model:
        Provider: BetterModel   # or ModelEngine
        Id: capybara            # the bundled model — MyPet installs it for you
```
{% endcode %}

The Chameleon is identical, with `Id: chameleon`:

{% code title="pet-config.yml" %}
```yaml
MyPet:
  Pets:
    Chameleon:
      Host: Ocelot
      HP: 20.0
      Speed: 0.3
      LeashItem: lead
      Model:
        Provider: BetterModel
        Id: chameleon
```
{% endcode %}

Then run **`/mypet reload config`** (no restart needed for a new creature).

## What happens on reload

Because the config now references a bundled model id, MyPet:

1. Copies `capybara.bbmodel` out of its own jar into the provider's folder — **only if the file is not already there**, so your own edited copy is never overwritten.
2. Runs that provider's reload (`bettermodel reload` / `meg reload`) once.
3. Registers `Capybara` as a real pet type, with its permission nodes (`mypet.leash.Capybara`, `mypet.command.trade.offer.Capybara`, …).

You should see this in console:

```
[MyPet] Installed bundled model 'capybara' into BetterModel.
```

If the provider is not installed, MyPet skips the copy silently — the pet type still registers, it just renders as a plain host mob.

## Get one in-game

Now that the type exists, all three normal routes work:

| Route        | How                                                                                                                                                                                                                                                                                        |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Admin**    | `/petadmin create <player> mypet:capybara` — needs `MyPet.admin.create`. Custom creatures use the **`mypet:`** namespace; vanilla types use `minecraft:`. Tab-completion suggests the full `mypet:capybara` form.                                                                          |
| **Pet shop** | Add `Capybara` to [`pet-shops.yml`](../../configuration/pet-shops.yml.md) with a price, like any other pet type.                                                                                                                                                                           |
| **Taming**   | A player leashes any mob already wearing the capybara model — one you spawn with `/bm spawn` (`/meg summon` on ModelEngine), or one MyPet left behind when a Capybara pet was released. Needs `mypet.leash.Capybara` and any [leash requirements](../leash-flags-requirements.md) you set. |

## Choosing a host

`Host:` is the vanilla mob whose movement, pathfinding, and physics the creature borrows — it is **not** visible to players, the model covers it completely. A flying host makes the pet fly; a swimming host makes it swim.

`Pig` and `Ocelot` above are only suggestions. Any walking mob works for both models. Changing `Host:` later requires a **server restart** (everything else applies on `/mypet reload config`).

## Which skilltrees they get

Both models are already wired into the [default skilltree set](../../../skilltree-creation/default-skilltrees.md) under those exact type names:

| Creature      | Bundled skilltrees that accept it                                                                                                                    |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Capybara**  | `Serenity` (its own signature tree), `Companion`, `Kindred`, and the amphibious `ShoreKeeper` / `ShorePathfinder` / `ShoreSteward` / `ShoreWayfarer` |
| **Chameleon** | `Camouflage` (its own signature tree), `Apex`, `Predator`, and the land `LandKeeper` / `LandPathfinder` / `LandSteward` / `LandWayfarer`             |

This is why the section name matters: skilltree eligibility is matched on the pet type name, so a differently-named section simply is not in those lists.

## Animations

Both bundled models already use MyPet's default animation names — `spawn`, `despawn`, `sit`, `sit_loop`, `unsit`, `attack` — plus `walk`, `run`, `idle`, and `jump` for the rendering plugin. Nothing to remap. See [Animations](./#animations).

## Troubleshooting

| Symptom                                                             | Cause and fix                                                                                                                                                           |
| ------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/petadmin create <player> mypet:capybara` says the type is invalid | No `Capybara` section in `pet-config.yml`, or it is missing the `Host:` key. A section without `Host:` is treated as settings for an existing type, not a new creature. |
| Pet spawns but looks like a pig                                     | BetterModel/ModelEngine is not installed, or the model failed to load. Check console for the `Installed bundled model` line and for provider errors.                    |
| The `.bbmodel` never appears in the provider folder                 | The installer only runs for `Provider: BetterModel` or `ModelEngine`. `ItemsAdder` and `MythicMobs` are skipped by design.                                              |
| Console: `duplicates the model of '<other>'`                        | Two sections use the same `Provider` + `Id`. A model is a creature's identity, so only one type may claim `capybara`.                                                   |
| Pet has no skilltrees to choose                                     | The section is not named exactly `Capybara` / `Chameleon`, or you replaced the bundled skilltrees. Add your type name to a tree's eligible mob types.                   |

## See also

* [Custom Pet Models](./) — the full feature, all six methods
* [pet-config.yml → Custom creature definitions](../../configuration/pet-config.yml/#custom-creature-definitions-host) — every key explained
