---
description: Player-facing commands and examples.
---

# Player Commands

### Legend

* `<option>` required
* `[option]` optional

Most commands have aliases (example: `/pi`). Prefer aliases.

### Commands

| Command                                                        | Description                                    |
| -------------------------------------------------------------- | ---------------------------------------------- |
| [`/mypet`](player-commands.md#mypet)                           | Show available MyPet commands                  |
| [`/petbeacon`](player-commands.md#petbeacon)                   | Open your pet’s beacon window                  |
| [`/petbehavior`](player-commands.md#petbehavior)               | Set your pet’s behavior mode                   |
| [`/petcall`](player-commands.md#petcall)                       | Teleport your pet to you                       |
| [`/petcapturehelper`](player-commands.md#petcapturehelper)     | Toggle CaptureHelper                           |
| [`/petchooseskilltree`](player-commands.md#petchooseskilltree) | Select a skilltree                             |
| [`/petinfo`](player-commands.md#petinfo)                       | Show info about your (or another player’s) pet |
| [`/petinventory`](player-commands.md#petinventory)             | Open your pet’s inventory                      |
| [`/petlist`](player-commands.md#petlist)                       | (TODO) Document this command                   |
| [`/petname`](player-commands.md#petname)                       | Set your pet’s name (supports colors)          |
| [`/petoptions`](player-commands.md#petoptions)                 | Client-side options (healthbar, idle volume)   |
| [`/petpickup`](player-commands.md#petpickup)                   | Toggle item pickup                             |
| [`/petrelease`](player-commands.md#petrelease)                 | Release your pet                               |
| [`/petrespawn`](player-commands.md#petrespawn)                 | Manage paid pet respawn behavior               |
| [`/petsendaway`](player-commands.md#petsendaway)               | Send your pet away (can be called back)        |
| [`/petsettings`](player-commands.md#petsettings)               | (TODO) Document this command                   |
| [`/petshop`](player-commands.md#petshop)                       | Open the pet shop GUI                          |
| [`/petskill`](player-commands.md#petskill)                     | Show skill info for your pet                   |
| [`/petstop`](player-commands.md#petstop)                       | Stop your pet attacking its target             |
| [`/petstore`](player-commands.md#petstore)                     | Store your active pet                          |
| [`/petswitch`](player-commands.md#petswitch)                   | Switch between pets                            |
| [`/pettrade`](player-commands.md#pettrade)                     | Offer your pet to another player               |

***

### mypet

Shows all available MyPet commands.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/mypet
```

***

### petbeacon

Opens the beacon window of your pet.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petbeacon
```

#### Aliases

* `/pbeacon`

***

### petbehavior

Sets your pet’s behavior mode.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petbehavior [mode]
```

#### Modes

* `friendly` (`friend`): pet will not fight, even when attacked
* `normal`: pet acts like a normal wolf
* `aggressive` (`aggro`): attacks everything within 15 blocks of owner
* `farm`: attacks every monster within 15 blocks of owner
* `raid`: like normal, but will not attack players and their minions
* `duel`: attacks other duel pets within 5 blocks

#### Aliases

* `/pb`
* `/petb`

***

### petcall

Teleports your pet to you.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petcall
```

#### Aliases

* `/pc`
* `/petc`

***

### petcapturehelper

Enables/disables the CaptureHelper.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petcapturehelper
```

#### Aliases

* `/pch`

***

### petchooseskilltree

Shows all available skilltrees and lets you pick one for your pet.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petchooseskilltree
```

#### Aliases

* `/pcst`
* `/petcst`

***

### petinfo

Shows details about your pet. You can target another player.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petinfo [username]
```

#### Output

* hit-points
* hunger
* food items
* behavior
* experience
* level
* owner (only when the pet isn’t yours)
* skilltree

#### Aliases

* `/pinfo`

***

### petinventory

Opens your pet’s inventory.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petinventory [playername]
```

#### Notes

* Opening another player’s pet inventory requires admin permissions.

#### Aliases

* `/pi`
* `/peti`

***

### petlist

(TODO) Add the syntax, output, and aliases for `/petlist`.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

***

### petname

Sets the name of your pet.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petname <new-pet-name>
```

<details>

<summary>Color placeholders</summary>

Use placeholders inside the name:

`<black>`, `<darkaqua>`, `<darkblue>`, `<darkgreen>`, `<darkred>`, `<darkpurple>`, `<gold>`, `<gray>`, `<darkgray>`, `<blue>`, `<green>`, `<aqua>`, `<red>`, `<lightpurple>`, `<yellow>`, `<white>`, `<magic>`, `<bold>`, `<strikethrough>`, `<underline>`, `<italic>`, `<reset>`

</details>

***

### petoptions

Client-side options.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petoptions <option> [parameters...]
```

#### Options

* `healthbar`: toggle actionbar healthbar on/off
* `idle-volume <percent>`: set idle sound volume

***

### petpickup

Toggles pet pickup on/off.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Notes

* Requires an inventory with at least one row of slots.

#### Usage

```
/petpickup
```

#### Aliases

* `/pp`
* `/petp`

***

### petrelease

Releases your pet. You will no longer have an active pet.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petrelease [pet-name]
```

***

### petrespawn

Controls paid respawn behavior.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petrespawn [pay|show|auto]
```

#### Notes

* `auto <seconds>` sets the max time you want to pay for.
* Example: `/petrespawn auto 10`. If the pet has 16s respawn time, the plugin waits until 10s remain. Then it respawns if you can pay.

#### Aliases

* `/petr`
* `/pr`

***

### petsendaway

Sends your pet away. You can call it back with `/petcall`.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petsendaway
```

#### Aliases

* `/psa`
* `/petsa`

***

### petsettings

(TODO) Add the syntax, options, and aliases for `/petsettings`.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

***

### petshop

Opens a GUI that shows available pet shops.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petshop [shopname]
```

#### Aliases

* `/petsh`
* `/psh`

***

### petskill

Shows info about your pet’s skills.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petskill [playername]
```

#### Notes

* Viewing other players’ pets may require admin permissions.

***

### petstop

Orders your pet to stop attacking its target.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Notes

* Not useful in `farm` and `aggressive` behavior modes.

#### Usage

```
/petstop
```

#### Aliases

* `/ps`
* `/pets`

***

### petstore

Stores your active pet. Retrieve it later via `/petswitch`.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petstore
```

#### Aliases

* `/pstore`
* `/pst`

***

### petswitch

Switch between pets.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/petswitch
```

#### Aliases

* `/pswitch`

***

### pettrade

Offers your current pet to another player.

{% include "../.gitbook/includes/player-only-command-no-console.md" %}

#### Usage

```
/pettrade [accept|reject|cancel|a <player name>] <price>
```

#### Notes

* `<price>` is any economy price.

#### Aliases

* `/pett`
* `/pt`
