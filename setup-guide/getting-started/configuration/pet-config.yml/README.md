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
