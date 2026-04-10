---
description: Learn the basics of MyPet
---

# Overview

MyPet is a Minecraft plugin that allows you to capture almost any mob as your Pet. You can train your Pet to fight with you, collect items, and more.

{% hint style="info" %}
This guide is **player-facing**. It assumes MyPet is already installed on the server you're playing on. If you are looking to install MyPet on your server, visit the [Setup Guide](https://app.gitbook.com/o/cEmGiPtUi9sbvpCRqMnM/s/bDDqqkbXYyKdy88rOP6U/). If MyPet isn't on the server you're playing on, ask an admin!
{% endhint %}

{% hint style="info" %}
This guide assumes that all settings have been left as default on the server you are playing on. Check with the server admins to see if there are any specific changes to the configuration on your sever.
{% endhint %}

### Capture a mob as your Pet

Before being able to capture a mob, you need to understand its capture requirements. Many mobs have the same capture requirement by default, but there are some exceptions - and server owners can always customize the requirements to better suit their server.

#### Pet Capture Helper

The easiest way to determine how to capture a mob as a Pet is to use the Pet Capture Helper (`/pch`). When enabled, mobs will display either red or green particles above their head based on whether they meet the requirements for being captured. Striking the mob with a lead (by default) will list the capture requirements in chat.

Once captured, your Pet will follow you around wherever you go!

### Skilltrees

Skilltrees are what allow your Pet to gain new skills and abilities.

Assign your Pet to a skilltree with `/pcst`. It’s an alias of [`/petchooseskilltree`](commands/player-commands.md#petchooseskilltree).

Pets gain XP when they kill mobs. They also gain some XP when you kill mobs.

### Equip your Pet

Some Pets can hold items or wear armor.

* Equip: sneak + right-click your pet with the item.
* Remove: sneak + right-click with **shears**.

### Name your Pet

Rename your Pet with [`/petname <name>`](commands/player-commands.md#petname).

### Pet behavior

Change how your Pet fights with [`/petbehavior`](commands/player-commands.md#petbehavior).

Behaviors unlock as your Pet levels based on the Skilltree your Pet has enabled.

* **Friendly**: won’t fight, even if attacked
* **Normal**: acts like a normal wolf
* **Aggressive**: attacks everything within 15 blocks of you
* **Farm**: attacks hostile mobs within 15 blocks of you
* **Raid**: won’t attack players or their pets
* **Duel**: attacks other duel pets within 5 blocks

### Feed your Pet

Feed your Pet to keep it alive. Hungry Pets are weaker and deal less damage.

Each Pet has specific food. Check it with [`/petinfo`](commands/player-commands.md#petinfo).

### Pet Storage

There are two different ways to store a Pet:

`/petsendaway` or `/psa` allows you to temporarily send your Pet away (similar to telling a dog to go sit in their kennel.) Your Pet can be recalled with `/petcall`, and while sent away, you cannot capture other Pets.

To store a Pet, use `/petstore` or `/pst`. This allows you to capture other Pets while your current Pet is stored. To switch between pets, use `/petswitch` or `/psw`.

### Useful commands

* Release a Pet forever: [`/petrelease`](commands/player-commands.md#petrelease)
* Stats + food: [`/petinfo`](commands/player-commands.md#petinfo)
* Skills overview: [`/petskill`](commands/player-commands.md#petskill)
* Behavior: [`/petbehavior`](commands/player-commands.md#petbehavior)
* Walking beacon: [`/petbeacon`](commands/player-commands.md#petbeacon)
