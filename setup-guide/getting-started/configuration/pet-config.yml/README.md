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

{% hint style="info" %}
**Since 4.0.1, a pet released on death drops its equipment.** Any armor or weapon the pet was wearing — gear it kept from taming (see [`RetainEquipmentOnTame`](#retainequipmentontame)), gear a horse or llama was given, or gear another plugin set through the API — now drops as items where the pet died. Previously this never happened: the drop was attempted, but an internal check could never pass for an already-dead pet, so the equipment was silently lost.
{% endhint %}

#### `RemoveAfterRelease`

* Type: boolean
* Description: Whether or not the Mob is deleted after the pet is released.

{% hint style="info" %}
This setting decides **where a released pet's equipment ends up**. Left at `false`, the pet becomes a live wild mob that keeps wearing its gear. Set to `true`, the mob is deleted and the gear drops as items instead. See [`RetainEquipmentOnTame`](#retainequipmentontame).
{% endhint %}

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

#### `RetainEquipmentOnTame`

* Type: boolean
* Default: `true`
* Description: When true, a wild mob leashed into a pet keeps the armor and weapons it was wearing, and that gear becomes the pet's own equipment — it stays with the pet, and it drops when the pet dies or is released. When false, those slots are emptied as the mob is tamed and the items drop on the ground where it stood.
* Restrictions: This setting can only be used with pet-types that can wear equipment.

{% hint style="info" %}
Only the slots a pet-type actually supports are touched. A `Fox` carries an item in its mouth, a `Zombie` wears the full humanoid set — anything the mob was wearing in a slot its pet-type doesn't support is left exactly as it is, whichever way you set this.

Vanilla per-slot drop chances play no part: if the gear is visible on the mob, taming keeps it (or drops it). There is no roll.
{% endhint %}

{% hint style="warning" %}
**Releasing a pet does not normally drop its gear — that is expected.**

With the default [`RemoveAfterRelease: false`](#removeafterrelease), `/petrelease` turns the pet back into a living wild mob, and that mob walks away **still wearing** the equipment. Nothing lands on the ground, because nothing was taken away.

Only with `RemoveAfterRelease: true` is the mob itself removed, and then the equipment drops as items at the release location. Either way the gear is never destroyed — it is on the mob or on the floor.
{% endhint %}

{% hint style="info" %}
**Pets created by other plugins are not affected by this setting.** A pet adopted from MythicMobs or a similar source plugin always keeps the gear that plugin gave it, whatever `RetainEquipmentOnTame` is set to. The setting applies to leash taming only.
{% endhint %}

#### `WillShake`

* Type: boolean
* Description: When false, the pet will not shake when outside of the nether/lava.
* Restrictions: This setting can only be used with hoglins, piglins, and piglin brutes.

## Custom Pet Models

MyPet supports custom BlockBench models through **ModelEngine**, **BetterModel**, and **ItemsAdder**, plus **MythicMobs** as a fourth custom-creature provider. There are three configuration shapes, all under `MyPet.Pets` in `pet-config.yml`:

* **Re-skin an existing type** — add a `Model:` block to a vanilla pet type.
* **Custom creature** — a `Host:` section with a `Model: { Provider, Id }` block. For ModelEngine/BetterModel/ItemsAdder, MyPet renders it, and — because the model is the identity — a mob wearing that model can be leashed straight back into the pet.
* **Custom Creature — MythicMobs** — `Host:` + `Model: { Provider: MythicMobs, Id: <mob-name> }`; MyPet spawns/adopts the real MythicMob.

For a feature overview and the six methods, see [Custom Pet Models](../../systems/custom-pet-models.md).

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
* Values: `ModelEngine`, `BetterModel`, `ItemsAdder`, `MythicMobs` (`MythicMobs` is only valid on custom creatures — see below — not on a re-skin)
* Description: Which provider supplies the model — a rendering plugin (ModelEngine/BetterModel/ItemsAdder) or the source creature plugin (MythicMobs).

#### `Model.Id`

* Type: string
* Description: The model id as registered in the provider — the ModelEngine/BetterModel model name, an ItemsAdder namespaced id such as `mypack:dragon`, or (for `Provider: MythicMobs`) the MythicMob's internal name.

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
* Description: The vanilla mob type whose movement, pathfinding, and physics the creature inherits. A flying host (e.g. `Phantom`, `Allay`) makes the pet fly; a swimming host makes it swim. Changing `Host:` requires a server restart. For `Provider: MythicMobs`, set `Host:` to the MythicMob's own base vanilla entity (a Phantom-based boss → `Host: Phantom`) — MyPet spawns/rebuilds from that type.

{% hint style="info" %}
**Skills for custom creatures** are granted through **skilltrees** — list the creature's type name in a skilltree's eligible mob types, exactly like vanilla pet types. There is no skill list directly in the creature definition.
{% endhint %}

{% hint style="info" %}
**Adding a new custom creature works with `/mypet reload config`** — a new `Host:` section is registered, and its stats and model load, on reload; no restart needed. Editing an existing creature's stats or `Model:` also applies on reload. The one exception is **changing an existing creature's `Host:`**, which still requires a restart (the host entity class is bound when the type is first registered).
{% endhint %}

{% hint style="info" %}
Selling a custom creature in a pet shop requires no extra fields here — add the creature id to `pet-shops.yml` with a price, description, and position just like any vanilla pet type.
{% endhint %}

{% hint style="info" %}
**Custom creatures are also tameable — no extra config.** Because a custom creature's model *is* its identity, any mob already wearing that model can be leashed straight into the pet (subject to the type's `LeashRequirements`): one you `/meg summon` / `/bm spawn` into the world, or one MyPet left behind when a pet of this type was released. You do **not** need a separate definition for ModelEngine / BetterModel / ItemsAdder / MythicMobs creatures — the `Provider:` + `Id:` type above handles both creating and taming, uniformly across all four providers.
{% endhint %}

{% hint style="warning" %}
**Each custom type needs a unique model.** Because the model is the pet's identity, two custom types must not share the same `Provider` + `Id` — MyPet couldn't tell which type a leashed modeled mob should become. If two types declare the same model, MyPet keeps the first and **skips** the later one on load (a warning names both in the console). Give each custom type its own `Model.Id`.
{% endhint %}

**MythicMobs works the same shape, with one difference under the hood.** For `Provider: MythicMobs`, MyPet doesn't draw a model on a vanilla host — it spawns (via `/petadmin create` / pet shop) or adopts (via leashing) the **real MythicMob**, model and all. `Id:` is the MythicMob's internal name, and (as with the other three providers) the section name is arbitrary:

{% code title="pet-config.yml" %}
```yaml
MyPet:
  Pets:
    FrostBoss:                    # arbitrary name — the mob's identity lives in Id
      Host: Phantom                # the MythicMob's base vanilla entity
      HP: 200.0
      Speed: 0.3
      LeashItem: lead
      LeashRequirements: [Tamed]
      Model:
        Provider: MythicMobs
        Id: MyDragonBoss           # the MythicMob's internal name
```
{% endcode %}

{% hint style="info" %}
**MythicMobs is spawned, not drawn.** MyPet doesn't render a MythicMob's model itself — it spawns/adopts the genuine MythicMob, so its model, AI, and abilities are the MythicMob's own. Releasing it respawns that same real MythicMob (not a bare vanilla animal). Taming also requires MythicMobs to allow it: set `Disable-Leashing: false` in the `MythicMobs:` section of [hooks-config.yml](../hooks-config.yml.md). The normal [leash requirements](../../systems/leash-flags-requirements.md) still apply.
{% endhint %}

### Model animations

MyPet plays a few **discrete animations** on a pet's model at the right moments. By default it plays animations named `spawn`, `despawn`, `sit`, `sit_loop`, `unsit`, and `attack` — so if your model uses those names, animations just work with no configuration. If a model names them differently (common for third-party MythicMobs/ItemsAdder models), remap them per type under an optional `Model.Animations` block. It works on **any** `Model:` block — re-skins and custom creatures alike, including MythicMobs.

{% code title="pet-config.yml" %}
```yaml
      Model:
        Provider: ModelEngine
        Id: frost_dragon
        Animations:            # all optional; an omitted event uses its default name
          attack: swoop        # play "swoop" instead of "attack" when the pet hits
          despawn: vanish
```
{% endcode %}

| Event      | Default name | When it plays |
| ---------- | ------------ | ------------- |
| `spawn`    | `spawn`      | When the pet is first summoned (not on chunk reload / relog). |
| `despawn`  | `despawn`    | When the pet is stored or removed (not on recall) — removal waits for the animation to finish. |
| `sit`      | `sit`        | When the pet sits down. |
| `sit_loop` | `sit_loop`   | Looped while the pet stays seated (started once `sit` has finished). |
| `unsit`    | `unsit`      | When the pet stands back up. |
| `attack`   | `attack`     | Each time the pet lands a melee hit or fires a ranged shot. |

{% hint style="info" %}
**Movement animations are not configured here.** Walking, running, idling, and jumping are driven automatically by the rendering plugin from the mob's movement — name them by your provider's own convention in the model itself. `Model.Animations` only covers the six discrete events above.
{% endhint %}

{% hint style="info" %}
Animations are **best-effort**: if a named animation isn't present in the model, MyPet simply skips it. For the despawn delay, providers that can't report an animation's length (BetterModel, ItemsAdder) fall back to a short fixed delay.
{% endhint %}

#### `Model.Animations.<event>`

* Type: string (one key per event: `spawn`, `despawn`, `sit`, `sit_loop`, `unsit`, `attack`)
* Required: No
* Description: Overrides the animation name MyPet plays for that event. Any omitted event uses its default name (identical to the event key). Applies to every provider alike, including MythicMobs.

### Acquiring custom creatures

* **Command:** `/petadmin create <player> mypet:<creature-id>` — requires permission `MyPet.admin.create`. (Vanilla pet types are created with the `minecraft:` namespace, e.g. `minecraft:wolf`; custom creatures use `mypet:`.) For a `Provider: MythicMobs` creature this spawns the genuine MythicMob.
* **Pet shop:** list the creature id in `pet-shops.yml` so players can buy it — MythicMobs creatures spawn/adopt the real MythicMob the same as any other custom creature.
* **Taming:** any mob already wearing the creature's model can be leashed straight into the pet, using the normal [leash requirement rules](../../systems/leash-flags-requirements.md) — a `/meg summon`/`/bm spawn` mob, one MyPet left behind on release, or (for MythicMobs) a wild MythicMob whose internal name matches the type's `Model.Id`. Taming a MythicMob also requires `Disable-Leashing: false` in the `MythicMobs:` section of [hooks-config.yml](../hooks-config.yml.md).

### Release behavior

What happens when a player uses `/petrelease` depends on how the pet was created:

* **Re-skinned vanilla pet (Path A):** releases as the underlying vanilla mob, same as always. The model is removed.
* **Rendered custom creature (Path B — ModelEngine/BetterModel/ItemsAdder):** a wild mob is left behind still wearing the model, so it can be re-leashed back into the same pet.
* **MythicMobs custom creature (Path C):** the genuine MythicMob is respawned at the release location — with its own AI, abilities, and model — and MyPet's host entity is removed.
* **Custom creature whose provider plugin is no longer installed:** the entity is simply despawned. No vanilla replacement is created.
