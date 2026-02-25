---
description: Contains options for pet types.
icon: paw
---

# pet-config.yml

The `pet-config.yml` file contains all MyPet-Type specific settings. All other settings can be found in the main [config.yml](config.yml.md).

## Structure

Configuration path:

```yaml
MyPet:
  Pets:
    <MyPet-Type-Name>:
```

Below are the settings available for each pet type.

### `HP`

* Type: double
* Description: The maximum HP the pet (type) has by default.

### `Speed`

* Type: double
* Description: The running speed the pet-type has by default.

{% hint style="warning" %}
Small changes have a massive impact on the speed.
{% endhint %}

### `Food`

* Type: list
* Description: The food this pet-type eats. This setting must be a list of valid [config items](custom-item-data-in-config.md).

### `LeashItem`

* Type: string
* Description: The item this pet-type can be leashed with. This setting must be a valid [config item](custom-item-data-in-config.md).

### `LeashRequirements`

* Type: list
* Description: A list of valid [Leash Requirements](../systems/leash-flags-requirements.md).

### `CustomRespawnTimeFactor`

* Type: int
* Description: This setting allows to change the respawn times for this pet-type. This value will be added on top of the value from the main config.

### `CustomRespawnTimeFixed`

* Type: int
* Description: This setting allows to change the respawn times for this pet-type. This value will be added on top of the value from the main config.

### `ReleaseOnDeath`

* Type: boolean
* Description: Whether or not the pet is released on death.

### `RemoveAfterRelease`

* Type: boolean
* Description: Whether or not the Mob is deleted after the pet is released.
