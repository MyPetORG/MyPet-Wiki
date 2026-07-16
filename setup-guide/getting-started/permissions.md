---
description: Every MyPet permission node, what it grants, and its default.
icon: user-lock
---

# Permissions

MyPet uses standard Bukkit permission nodes, so any permission plugin
(LuckPerms, etc.) can manage them. This page lists every node, what it grants,
and its default, grouped by who it's meant for.

### How defaults work

Each node has one of two behaviours out of the box:

* **Bundled into `mypet.player`** — granted to normal players automatically when
  you give a group the `mypet.player` bundle. This is the everyday player toolkit.
* **`default: op`** — only operators (or players you grant it to explicitly)
  have it. All admin and bypass nodes are `op`-only, so ordinary players never
  get them by accident.

Two umbrella nodes cover the common cases:

* **`mypet.player`** — the normal-player bundle (see [Player permissions](#player-permissions)).
* **`mypet.admin`** — the full admin bundle; grants every admin, bypass, and
  storage node listed under [Admin permissions](#admin-permissions).

Grant the umbrella for convenience, or grant individual child nodes for
least-privilege setups.

## Player permissions

### The `mypet.player` bundle

Granting `mypet.player` gives a player the standard toolkit:

| Node | Grants |
| ---- | ------ |
| `mypet.leash.*` | Leash (tame) every pet type. |
| `mypet.command.respawn` | `/petrespawn` |
| `mypet.command.release` | `/petrelease` |
| `mypet.command.capturehelper` | The CaptureHelper. |
| `mypet.command.name` | `/petname` |
| `mypet.command.name.color` | Use colours in pet names. |
| `mypet.command.name.format` | Use formatting tags (bold, italic, …) in pet names. |
| `mypet.command.options` | The MyPet options command. |
| `mypet.command.trade.offer.*` | Offer any pet type for trade. |
| `mypet.command.trade.receive.*` | Receive any pet type in a trade. |
| `mypet.command.list` | `/petlist` (own pets). |

Other player command nodes (`mypet.command.switch`, `mypet.command.store`,
`mypet.command.info.other`) are declared separately and can be granted as needed.

### Extended permissions

**Extended permissions are _not_ part of the `mypet.player` bundle** — grant them
explicitly to unlock the matching capability. This lets you sell/gate features
per rank.

| Node | Grants |
| ---- | ------ |
| `mypet.extended.feed` | Feed pets. |
| `mypet.extended.equip` | Equip pets. |
| `mypet.extended.beacon` | Open the beacon GUI. |
| `mypet.extended.inventory` | Open the pet's inventory (backpack). |
| `mypet.extended.ride` | Mount pets. |
| `mypet.extended.ride.fly` | Fly the pet while riding. |
| `mypet.extended.control` | Control (walk) pets. |
| `mypet.extended.pickup` | Enable item pickup. |
| `mypet.extended.behavior.friendly` | Use the `friendly` behavior. |
| `mypet.extended.behavior.aggressive` | Use the `aggressive` behavior. |
| `mypet.extended.behavior.farm` | Use the `farm` behavior. |
| `mypet.extended.behavior.raid` | Use the `raid` behavior. |
| `mypet.extended.behavior.duel` | Use the `duel` behavior. |

### Per-pet-type nodes

`mypet.leash.*` and the trade wildcards each expand into one child node **per pet
type**, registered automatically at runtime — including pet types added by
third-party plugins. Grant a single type instead of the wildcard to restrict
players to specific mobs:

| Pattern | Grants |
| ------- | ------ |
| `mypet.leash.<PetType>` | Leash only that pet type (e.g. `mypet.leash.Wolf`). |
| `mypet.command.trade.offer.<PetType>` | Offer only that pet type for trade. |
| `mypet.command.trade.receive.<PetType>` | Receive only that pet type in a trade. |

`<PetType>` is the internal type name (e.g. `Wolf`, `Creeper`, `Creaking`).

### Experience multipliers

When the `PERMISSION` experience modifier is enabled in the config, a player's
pet earns bonus experience based on a `mypet.experience.multiplier.<percent>`
node. **Any positive integer works**, and the **highest** matching node wins —
the declared examples below are just presets.

| Node | Effect |
| ---- | ------ |
| `mypet.experience.multiplier.125` | +25% experience (1.25×). |
| `mypet.experience.multiplier.150` | +50% experience (1.50×). |
| `mypet.experience.multiplier.175` | +75% experience (1.75×). |
| `mypet.experience.multiplier.200` | +100% experience (2.00×). |
| `mypet.experience.multiplier.225` | +125% experience (2.25×). |
| `mypet.experience.multiplier.250` | +150% experience (2.50×). |

The `<percent>` is applied as `percent / 100`, so `.183` → 1.83× and `.50` →
0.5× (halved). If the modifier is disabled or the owner is offline, experience
passes through unchanged.

### Storage limit

The number of pets a player may **store** is capped by their highest
`mypet.petstorage.limit.<X>` node.

| Node | Effect |
| ---- | ------ |
| `mypet.petstorage.limit.<X>` | Store up to `X` pets. `X` must be ≤ the `mypet.Max-Stored-Pet-Count` [config value](configuration/config.yml.md#max-stored-pet-count). |
| `mypet.petstorage.limit.*` | `default: op` · granted by `mypet.admin` · store the configured maximum (unlimited tier). |

See [Pet Storage](systems/pet-storage.md) for the full explanation.

### Skilltree access

A skilltree can require a permission before a player may use it. The node is
derived from the skilltree (or the value of its permission requirement):

| Pattern | Grants |
| ------- | ------ |
| `mypet.skilltree.<name>` | Access the skilltree `<name>` (when it has a permission requirement). |

See [Skilltrees](systems/skilltrees.md) and the skilltree
[Requirements](../skilltree-creation/creating-custom-skilltrees/requirements.md).

## Admin permissions

### The `mypet.admin` bundle

`mypet.admin` (`default: op`) is an **umbrella node** that grants every admin,
bypass, and storage node below. Grant it for full admin capability, or grant
individual children for least-privilege delegation.

{% hint style="info" %}
No code path checks the bare `mypet.admin` node for behaviour — it is purely a
bundle. The old `isMyPetAdmin()` API method was removed; these granular nodes
replace it.
{% endhint %}

### `/mypet` subcommands

| Node | Command / action |
| ---- | ---------------- |
| `mypet.admin.editor` | `/mypet editor` — open the web editor. |
| `mypet.admin.reload` | `/mypet reload` |
| `mypet.admin.ticket` | `/mypet ticket` |
| `mypet.admin.update` | `/mypet update` |

### `/petadmin` subcommands

| Node | Subcommand |
| ---- | ---------- |
| `mypet.admin.clone` | `clone` |
| `mypet.admin.create` | `create` |
| `mypet.admin.exp` | `exp` |
| `mypet.admin.exprate` | `exprate` |
| `mypet.admin.info` | `info` |
| `mypet.admin.name` | `name` |
| `mypet.admin.npc` | `npc` |
| `mypet.admin.purge` | `purge` |
| `mypet.admin.remove` | `remove` |
| `mypet.admin.respawn` | `respawn` |
| `mypet.admin.skilltree` | `skilltree` |
| `mypet.admin.switch` | `switch` |

### Acting on other players' pets

These let a moderator run standard pet commands targeting **another player's**
pet:

| Node | Command |
| ---- | ------- |
| `mypet.command.info.other` | `/petinfo <player>` |
| `mypet.command.list.other` | `/petlist <player>` |
| `mypet.command.skill.other` | `/petskill <player>` |
| `mypet.command.inventory.other` | `/petinventory <player>` |
| `mypet.command.sendaway.other` | `/petsendaway <player>` |

### Notification node

| Node | Effect |
| ---- | ------ |
| `mypet.admin.notify` | Receive in-game notifications when a web-editor session (`/mypet editor`) applies changes. |

## Bypass permissions

Bypass nodes exempt a player from a normal gameplay restriction. All are
`default: op` and are granted by the `mypet.admin` bundle, so existing admins
are unaffected.

| Node | Effect |
| ---- | ------ |
| `mypet.bypass.skilltree` | Skip automatic skilltree assignment and the choose-only-once lock. |
| `mypet.bypass.fee` | Exempt from the skilltree switch fee (unless `Skilltree.SwitchFeeAdmin` is set). |
| `mypet.bypass.death` | Exempt from release-on-death and backpack-drop-on-death. |
| `mypet.bypass.inventory` | Open your own pet's backpack without `mypet.extended.inventory`. |
| `mypet.bypass.creative` | Use the pet backpack and pickup in Creative mode even when `Backpack.OpenInCreative` is disabled. |

## NPC nodes

Used with the [MyPet-NPC](plugin-hooks/citizens-npc.md) Citizens integration:

| Node | Effect |
| ---- | ------ |
| `mypet.npc.shop` | Use a pet-shop NPC. |
| `mypet.npc.storage` | Use a pet-storage NPC. |
