---
description: >-
  Skilltree requirements are used to limit skilltrees to pets that meet certain
  conditions.
icon: diamond-exclamation
---

# Requirements

<figure><img src="../../.gitbook/assets/Skilltree Requirements.png" alt="The Requirements section, which allows you to configure requirements that must be met in order to be able to use the skilltree." width="563"><figcaption></figcaption></figure>

The `Requirements` section of the [Configurator's](./) Inspector allows you to configure optional requirements that must be met in order to be able to use the skilltree.

### Requirements List

#### `NoSkilltree`

* Limits this skilltree to pets that have no skilltree yet.

#### `Skilltree`

* Limits this skilltree to pets that have a certain skilltree.
* Requires the skilltree name as a parameter.
* Example:
  * `Skilltree:Ride`

#### `Permission`

* Limits this skilltree to pets where the owner needs the `MyPet.skilltree.<skilltreename>` permission.
* The permission node can be changed by providing a parameter.
* Example:
  * `Permission:newNode` will become `MyPet.skilltree.newNode`.

#### `PetLevel`

* Limits this skilltree to pets that have a certain level.
* Can be limited to:
  * a specific level
  * a minimum level
  * a maximum level
* Examples:

```
PetLevel:min=2
PetLevel:min=2:max=4
PetLevel:max=2
PetLevel:3
```
