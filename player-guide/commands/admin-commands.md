---
description: Administrative commands and examples.
---

# Admin Commands

### Commands

| Command                                                 | Description                                             |
| ------------------------------------------------------- | ------------------------------------------------------- |
| [`/petadmin`](admin-commands.md#petadmin)               | Admin toolbox command (rename, exp, create, cleanup, …) |
| [`/petinventory`](admin-commands.md#petinventory-admin) | Open another player’s pet inventory                     |
| [`/petskill`](admin-commands.md#petskill-admin)         | View another player’s pet skill info                    |

***

### petadmin

Admin toolbox for managing pets.

#### Usage

```
/petadmin <option> [parameters...]
```

#### Permission

* `MyPet.admin`

#### Options

**name**

Set the name of a pet for a specific player.

```
/petadmin name <ownername> <new petname>
```

**exp**

Set a pet’s XP for a specific player.

```
/petadmin exp <ownername> <new exp of the pet> [add|set|remove]
```

**respawn**

Set or display a pet’s respawn time.

Notes:

* Only changes respawn time for **dead** pets.

```
/petadmin respawn <ownername> [new respawntime]
/petadmin respawn <ownername> [show]
```

**reload**

Reload selected config files.

```
/petadmin reload all
/petadmin reload config
/petadmin reload skilltrees
```

**skilltree**

Change the skilltree of a pet.

```
/petadmin skilltree <pet ownername> <skilltree>
```

**build**

Show the MyPet version and build number.

```
/petadmin build
```

**create**

Create a new pet for a specific player.

Notes:

* Not usable when the player already has an active pet.
* Use `-f` to force creation even if the player has a pet.
* Use TAB to see valid parameters for the selected pettype.

```
/petadmin create [-f] <ownername> <pettype> [parameter]
```

**clone**

Clone a pet from one player and give it to another.

```
/petadmin clone <pet ownername> <new pet ownername>
```

**remove**

Delete a specific player’s pet.

```
/petadmin remove <ownername>
```

**cleanup**

Delete unused pets older than a certain amount of time.

Notes:

* If no parameter is given, it cleans up pets unused since upgrading to MyPet 1.1.3.

```
/petadmin cleanup [1Y] [1D] [1H] [1M]
```

**ticket**

Create a ZIP file with info needed for developer support.

```
/petadmin ticket
```

**info item**

Log the item you’re holding, including NBT data. Useful for configuring items in MyPet config.

```
/petadmin info item
```

***

### petinventory (admin)

Open another player’s pet inventory.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petinventory <playername>
```

#### Permission

* `MyPet.admin`

#### Aliases

* `/pi`
* `/peti`

***

### petskill (admin)

View skill info for another player’s pet.

#### Usage

```
/petskill <playername>
```

#### Notes

* This requires admin permissions on most servers.

***

### Permissions

#### Bundle node

`MyPet.admin` is an **umbrella node** that grants every granular admin node listed below. Grant `MyPet.admin` to give a player complete admin capability; grant individual nodes for least-privilege delegation.

#### `/mypet` admin subcommands

| Permission node          | Command / action               |
| ------------------------ | ------------------------------ |
| `MyPet.admin.editor`     | `/mypet editor` — open the web editor |
| `MyPet.admin.reload`     | `/mypet reload`                |
| `MyPet.admin.ticket`     | `/mypet ticket`                |
| `MyPet.admin.update`     | `/mypet update`                |

#### `/mypetadmin` subcommands

| Permission node            | Subcommand    |
| -------------------------- | ------------- |
| `MyPet.admin.clone`        | `clone`       |
| `MyPet.admin.create`       | `create`      |
| `MyPet.admin.exp`          | `exp`         |
| `MyPet.admin.exprate`      | `exprate`     |
| `MyPet.admin.info`         | `info`        |
| `MyPet.admin.name`         | `name`        |
| `MyPet.admin.npc`          | `npc`         |
| `MyPet.admin.purge`        | `purge`       |
| `MyPet.admin.remove`       | `remove`      |
| `MyPet.admin.respawn`      | `respawn`     |
| `MyPet.admin.skilltree`    | `skilltree`   |
| `MyPet.admin.switch`       | `switch`      |

#### Act on other players’ pets

These nodes allow a player to run standard pet commands targeting another player’s pet:

| Permission node                    | Command                      |
| ---------------------------------- | ---------------------------- |
| `MyPet.command.info.other`         | `/petinfo <player>`          |
| `MyPet.command.list.other`         | `/petlist <player>`          |
| `MyPet.command.skill.other`        | `/petskill <player>`         |
| `MyPet.command.inventory.other`    | `/petinventory <player>`     |
| `MyPet.command.sendaway.other`     | `/petsendaway <player>`      |

#### Capability / bypass nodes

* `MyPet.admin` — full admin capability: bypasses the stored-pet count limit and unlocks the admin sections of the pet menu.
* `MyPet.admin.notify` — receive in-game notifications when a web-editor session applies changes.

### Bypass permissions

These exempt a player from a normal gameplay restriction. All are `default: op`
and are granted by the `MyPet.admin` bundle, so existing admins are unaffected.

| Node | Effect |
|------|--------|
| `MyPet.bypass.skilltree` | Skip automatic skilltree assignment and the choose-only-once lock. |
| `MyPet.bypass.fee` | Exempt from the skilltree switch fee (unless `Skilltree.SwitchFeeAdmin` is set). |
| `MyPet.bypass.death` | Exempt from release-on-death and backpack-drop-on-death. |
| `MyPet.bypass.inventory` | Open your own pet's backpack without `MyPet.extended.inventory`. |
| `MyPet.bypass.creative` | Use the pet backpack and pickup in Creative mode even when `Backpack.OpenInCreative` is disabled. |
| `MyPet.petstorage.limit.*` | Store the configured maximum number of pets (unlimited tier). |

> The `isMyPetAdmin()` API method was removed; these nodes replace it. No code
> path checks the bare `MyPet.admin` node anymore — it is purely a bundle.