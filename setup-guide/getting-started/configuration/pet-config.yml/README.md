---
description: Contains options for pet types.
icon: paw
---

# pet-config.yml

The `pet-config.yml` file contains all MyPet-Type specific settings. All other settings can be found in the main [config.yml](../config.yml.md).

For the default settings of this file see [Default Pet Settings](default-pet-settings.md).

### Structure

Configuration path:

```yaml
MyPet:
  Pets:
    <MyPet-Type-Name>:
```

### Common Settings

These are settings common to all pet-types.

#### `HP`

* Type: double
* Description: The maximum HP the pet (type) has by default.

#### `Speed`

* Type: double
* Description: The running speed the pet-type has by default.

{% hint style="warning" %}
Small changes have a massive impact on the speed.
{% endhint %}

#### `Food`

* Type: list
* Description: The food this pet-type eats. This setting must be a list of valid [config items](../custom-item-data-in-config.md).

#### `LeashItem`

* Type: string
* Description: The item this pet-type can be leashed with. This setting must be a valid [config item](../custom-item-data-in-config.md).

#### `LeashRequirements`

* Type: list
* Description: A list of valid [Leash Requirements](../../systems/leash-flags-requirements.md).

#### `CustomRespawnTimeFactor`

* Type: int
* Description: This setting adds an additional multiplier for a pet's respawn time. This value will be added on top of the value from the main config.

#### `CustomRespawnTimeFixed`

* Type: int
* Description: This setting allows you to change the respawn times for this pet-type. This value will be added on top of the value from the main config.

#### `ReleaseOnDeath`

* Type: boolean
* Description: Whether or not the pet is released on death.

#### `RemoveAfterRelease`

* Type: boolean
* Description: Whether or not the Mob is deleted after the pet is released.

### Specific Settings

These settings only apply to specific pet-types.

#### `CanBeSheared`

* Type: boolean
* Description: When true and when wool is present, gives wool when right clicked shears.
* Restrictions: This setting can only be used with the `Sheep` pet.

#### `CanGlide`

* Type: boolean
* Description: When true, allows the pet to glide around the player instead of being grounded.
* Restrictions: This setting can only be used with pet-types that naturally fly or hover.

#### `CanGiveMilk`

* Type: boolean
* Description: When true, returns a bucket of milk when right clicked with an empty bucket.
* Restrictions: This setting can only be used with the `Cow` pet.

#### `CanGiveStew`

* Type: boolean
* Description: When true, returns a bowl of stew when right clicked with a wooden bowl.
* Restrictions: This setting can only be used with the `Mooshroom` pet.

#### `CanLayEggs`

* Type: boolean
* Description: When true, the pet can lay eggs.
* Restrictions: This setting can only be used with the adult `Chicken` pet.

#### `CanOxidize`

* Type: boolean
* Description: When true, allows copper golem pets to oxidize.
* Restrictions: This setting can only be used with the `CopperGolem` pet.

#### `CanRegrowWool`

* Type: boolean
* Description: When true, allows a shorn sheep pet to regrow its wool.
* Restrictions: This setting can only be used with the `Sheep` pet.

#### `CanTossUp`

* Type: boolean
* Description: When true, allows the Iron Golem to toss up its target similar to vanilla behavior.
* Restrictions: This setting can only be used with the `IronGolem` pet.

#### `FixSnowTrack`

* Type: boolean
* Description: When true, cleans up snow trails from Snowman pets.
* Restrictions: This setting can only be used with the `Snowman` pet.

#### `GrowUpItem`

* Type: string
* Description: The item that can be used to turn a baby pet-type into an adult. This setting must be a valid [config item](../custom-item-data-in-config.md).
* Restrictions: This setting can only be used with pet-types that have baby variants.

#### `OxidationTime`

* Type: int
* Description: The time it takes for the pet to progress to the next oxidation level.
* Restrictions: This setting can only be used with the `CopperGolem` pet.

#### `WillShake`

* Type: boolean
* Description: When false, the pet will not shake when outside of the nether/lava.
* Restrictions: This setting can only be used with hoglins, piglins, and piglin brutes.

## Custom Pet Models

MyPet supports custom BlockBench models through **ModelEngine**, **BetterModel**, and **ItemsAdder**, plus tameable creatures from **MythicMobs**/ItemsAdder. There are three configuration shapes, all under `MyPet.Pets` in `pet-config.yml`:

* **Re-skin an existing type** — add a `Model:` block to a vanilla pet type.
* **Custom creature MyPet renders** — a `Host:` section with a `Model: { Provider, Id }` block.
* **Tameable creature** — a `Host:` section with a `Model: { Source }` marker; the model comes from the leashed MythicMobs/ItemsAdder creature.

For a feature overview and the seven supported combinations, see [Custom Pet Models](../../systems/custom-pet-models.md).

### Re-skin an existing pet type (`Model:`)

Add an optional `Model:` block to any existing pet type's section to make every pet of that type render with a custom model:

{% code title="pet-config.yml" %}
```yaml
MyPet:
  Pets:
    Wolf:
      HP: 20.0
      # ...other existing settings...
      Model:
        Provider: BetterModel      # ModelEngine | BetterModel | ItemsAdder
        Id: dragon                 # the model id in that provider
        NameHeight: 2.0            # optional; default = host mob height + 0.5
```
{% endcode %}

No per-pet setup is needed — the `Model:` block applies to the type. Editing it and reloading is all that is required to change which model a pet type uses.

#### `Model.Provider`

* Type: string
* Values: `ModelEngine`, `BetterModel`, `ItemsAdder`
* Description: Which rendering plugin supplies the model.

#### `Model.Id`

* Type: string
* Description: The model id as registered in the provider (ModelEngine/BetterModel model name, or ItemsAdder namespaced id such as `mypack:dragon`).

#### `Model.NameHeight`

* Type: double
* Required: No
* Description: Height in blocks at which the pet's floating name is shown above the model. Defaults to the host mob's height + 0.5. Raise this for tall models so the name sits just above them.

### Custom creature definitions (`Host:`)

A `MyPet.Pets.<Name>` section becomes a **custom creature** (rather than a settings override for a vanilla type) when it contains a `Host:` key. The creature has no vanilla equivalent — it is its own pet type. It supports the same common settings as any pet type (`HP`, `Speed`, `Food`, `LeashItem`, `LeashRequirements`, etc.) plus `Host:` and `Model:`:

{% code title="pet-config.yml" %}
```yaml
MyPet:
  Pets:
    FrostDragon:
      Host: Phantom                 # vanilla mob = movement profile (Phantom flies)
      HP: 80.0
      Speed: 0.3
      Food: [BEEF]
      LeashItem: lead
      Model:
        Provider: ModelEngine
        Id: frost_dragon
        NameHeight: 3.0
```
{% endcode %}

#### `Host:`

* Type: string
* Required: Yes (for custom creatures)
* Description: The vanilla mob type whose movement, pathfinding, and physics the creature inherits. A flying host (e.g. `Phantom`, `Allay`) makes the pet fly; a swimming host makes it swim. Changing `Host:` requires a server restart.

{% hint style="info" %}
**Skills for custom creatures** are granted through **skilltrees** — list the creature's type name in a skilltree's eligible mob types, exactly like vanilla pet types. There is no skill list directly in the creature definition.
{% endhint %}

{% hint style="info" %}
**Adding a new custom creature works with `/mypet reload config`** — a new `Host:` section is registered, and its stats and model load, on reload; no restart needed. Editing an existing creature's stats or `Model:` also applies on reload. The one exception is **changing an existing creature's `Host:`**, which still requires a restart (the host entity class is bound when the type is first registered).
{% endhint %}

{% hint style="info" %}
Selling a custom creature in a pet shop requires no extra fields here — add the creature id to `pet-shops.yml` with a price, description, and position just like any vanilla pet type.
{% endhint %}

### Tameable modeled creatures (source-driven)

To let players **leash a modeled creature that already exists in the world** — a MythicMobs mob or an ItemsAdder creature — and keep its model, define a **source-driven** custom creature: a `Host:` section whose `Model:` block uses a `Source:` marker instead of `Provider:`/`Id:`.

Three things must line up:

* **Section name = the source creature's id.** The MythicMobs internal name, or the ItemsAdder entity id (the part after the namespace — e.g. `phoenix` for `mypack:phoenix`). This is how MyPet recognises the leashed creature and how it respawns the genuine creature on release.
* **`Host:` = the source creature's base vanilla mob.** The model rides on the tamed entity, and on respawn MyPet rebuilds it from that base type — so `Host:` must match what the MythicMob/ItemsAdder creature is built on (a Phantom-based boss → `Host: Phantom`). A mismatch makes the pet fall back to a bare host with no model.
* **`Model.Source:`** marks the type as source-driven so the inherited model is kept (not stripped) each time the pet spawns.

{% code title="pet-config.yml" %}
```yaml
MyPet:
  Pets:
    MyDragonBoss:                 # must match the MythicMob internal name / ItemsAdder entity id
      Host: Phantom               # the vanilla mob the source creature is built on
      HP: 200.0
      Speed: 0.3
      LeashItem: lead
      Model:
        Source: MyDragonBoss      # marks this type source-driven; model comes from the tamed creature
```
{% endcode %}

A source-driven type has **no `Provider:`/`Id:`** — the model belongs to the tamed creature and is drawn by whatever engine that creature already uses (ModelEngine or BetterModel for MythicMobs; ItemsAdder for its own creatures). MyPet does not render it.

#### `Model.Source`

* Type: string
* Required: Yes (for tameable / source-driven creatures)
* Description: Marks the pet type as source-driven — its model is inherited from the leashed source creature rather than rendered by MyPet. Set it to the source creature's id (the value documents intent; its presence is what activates source-driven behavior). Mutually exclusive with `Provider:`/`Id:`.

{% hint style="info" %}
Taming also requires the source plugin to allow it. For MythicMobs set `Disable-Leashing: false` in the `MythicMobs:` section of [hooks-config.yml](../hooks-config.yml.md). The normal [leash requirements](../../systems/leash-flags-requirements.md) still apply.
{% endhint %}

### Acquiring custom creatures

* **Command:** `/petadmin create <player> mypet:<creature-id>` — requires permission `MyPet.admin.create`. (Vanilla pet types are created with the `minecraft:` namespace, e.g. `minecraft:wolf`; custom creatures use `mypet:`.)
* **Pet shop:** list the creature id in `pet-shops.yml` so players can buy it.
* **Taming:** if the creature is defined as [source-driven](#tameable-modeled-creatures-source-driven) (section name matching a MythicMob internal name or ItemsAdder creature id, with a `Model.Source` marker), players can [leash](../../systems/leash-flags-requirements.md) a wild instance of it using the normal leash rules.

### Release behavior

What happens when a player uses `/mypet release` depends on how the pet was created:

* **Re-skinned vanilla pet (Path A):** releases as the underlying vanilla mob, same as always. The model is removed.
* **Custom creature whose id matches a MythicMob or ItemsAdder creature:** the genuine source creature is respawned at the release location — with its own AI, abilities, and model — and MyPet's host entity is removed.
* **Custom creature with no matching source plugin:** the entity is simply despawned. No vanilla replacement is created.
