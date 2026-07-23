---
description: >-
  MyPet 4 ships with 124 default skilltrees arranged as a two-tier "Ascension
  Ladder". They are ordinary skilltree files; customize or replace them freely.
icon: stairs
---

# Default Skilltrees

MyPet 4 replaces the five classic default skilltrees of MyPet 3 (Combat, Farm, PvP, Ride and Utility) with **124 new skilltrees**. The old trees were identical for every pet; the new set gives each pet type its own small selection that fits its place in Minecraft's lore. No skilltree in the default set is available to every pet type.

{% hint style="success" %}
**The default skilltrees are content, not a system.** They are plain `.st.json` files built from the same building blocks as any [custom skilltree](creating-custom-skilltrees/) — [requirements](creating-custom-skilltrees/requirements.md), levels, [inheritance and weights](creating-custom-skilltrees/properties.md). Nothing about the two-tier "ascension" design is required by the plugin: you can edit any tree, delete the ones you don't want, or replace the entire set with your own flat MyPet-3-style trees. See [Using your own design instead](default-skilltrees.md#using-your-own-design-instead).
{% endhint %}

## The Ascension Ladder

A pet climbs the ladder in two steps: it picks a **role** at level 1 and **ascends** at level 20.

### Tier 1 — Role paths (Level 1)

A fresh pet (one that has no skilltree yet) can pick one of three paths:

| Path         | Trees                                                                                                                                                                                  | Typical skills                                                                                       |
| ------------ |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ---------------------------------------------------------------------------------------------------- |
| **Combat**   | The pet's lore family - _Undead_, _Arthropod_, _Illager_, _Construct_, _Nether_ or _End_ - or, for pets without such a family, a temperament tree: _Predator_, _Companion_ or _Rascal_ | Family-flavored combat, e.g. Wither + Slow for Undead, Poison for Arthropod, Fire + Knockback for Nether |
| **Utility**  | A _Keeper_ tree matching the pet's habitat (Land, Sky, Aquatic or Amphibious)                                                                                                          | Backpack, Pickup, Beacon                                                                              |
| **Mobility** | A _Wayfarer_ tree matching the pet's habitat                                                                                                                                           | Ride, Sprint                                                                                          |

Tier 1 trees stop at **level 25** and show a notification at level 19 hinting at the coming ascension.

### Tier 2 — Ascension (Level 20)

From level 20 on, the pet chooses between exactly two trees:

* **✦ Species signature** - a unique tree for the pet's species (90 of them, one per pet type, marked with a glowing icon). It carries the pet from level 20 to 100 and defines what makes that species special.
* **Path ascension** - a direct continuation of the chosen tier 1 tree (17 of them, one per tier 1 tree, built with [Inheritance](creating-custom-skilltrees/properties.md#inheritance)). This is also the safety net: a custom pet type added by a third-party plugin has no signature tree but can still ascend.

Ascending is **free** and **permanent**:

* No [switch fee](../getting-started/configuration/config.yml.md#skilltree) is charged, and ascending works even when `ChooseOnce` is enabled. Both exemptions are controlled by the `MyPet.Skilltree.FreeAscension` config option (on by default). Lateral switches between tier 1 trees still pay the normal fee.
* After ascending, the tier 1 trees disappear from the menu and cannot be selected again. The choice between signature and path ascension is final.

### Design principles behind the default set

* **In-universe.** Every tree is named and themed to fit in with Minecraft lore.
* **No universal trees.** Every tree's [eligible pets](creating-custom-skilltrees/eligible-pets.md) list is a real subset of the roster.
* **Vanilla parity.** Stronger vanilla mobs get stronger trees; a Warden's signature outclasses a Chicken's by design.
* **One signature per species.** Each pet type has exactly one tree that exists only for it; everything else is shared by family or habitat.

## How ascension works under the hood

There is no hardcoded ascension mechanic. The ladder is assembled entirely from standard skilltree features:

* Tier 1 trees use the [`NoSkilltree` requirement](creating-custom-skilltrees/requirements.md#noskilltree) and `MaxLevel: 25`.
* Tier 2 trees use `RequiredLevel: 20` and a [`Skilltree` requirement](creating-custom-skilltrees/requirements.md#skilltree) listing the tier 1 trees they accept.
* A switch counts as an "ascension" whenever the target tree's `Skilltree` requirement names the pet's **current** skilltree - that is exactly what `FreeAscension` waives the fee for. Your own custom trees get the same behavior if (and only if) they use the same pattern.
* Tier 1 trees carry per-pet-type [`Weight`](creating-custom-skilltrees/properties.md#weight) values, so servers using `RandomAssignment` see fitting picks (mount species lean toward their _Wayfarer_ tree, hostile mobs toward their combat tree).

{% hint style="warning" %}
If you disable `MyPet.Skilltree.PreventLevellingWithout`, a pet can level past 25 without ever picking a tree. It is then locked out of the entire default set: tier 1 trees are capped at level 25, and tier 2 trees require a previous skilltree. Keep that option enabled while using the default trees, or raise the tier 1 `MaxLevel` in your copies.
{% endhint %}

## Using your own design instead

The default trees are copied into `plugins/MyPet/skilltrees/` **only when that folder is first created**. After that, the folder is yours:

* **Edit or delete** any `.st.json` file. Deleted files are not re-created; only deleting the whole `skilltrees` folder triggers a fresh copy of the defaults on the next start.
* **Replace the set entirely** with your own trees. Single-tier, three-tier, one tree for everything: any structure that [Creating Custom Skilltrees](creating-custom-skilltrees/) can express is fine. The ascension behavior only activates for trees that opt into the `Skilltree` requirement pattern described above.
* **Edit in the browser** with the [Configurator](../configurator/) via `/mypet editor`.
* **Upgrading from MyPet 3?** Existing servers are untouched: your old `skilltrees` folder keeps working as-is, including the five classic trees. They are simply no longer bundled for new installs. See [Updating from MyPet 3 to 4](../getting-started/updating-from-3-to-4.md).
