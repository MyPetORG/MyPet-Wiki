---
description: The MyPet storage is way to have more than one MyPet.
icon: table-cells-row-unlock
---

# Pet Storage

Pet Storage allows you to store additional pets and activate them later as needed. Only one pet can be active at a time.

### What uses the storage?

* The pet [shop](https://wiki.mypet-plugin.de/misc/premium).
* The `/petstore` and `/petswitch` [commands](https://wiki.mypet-plugin.de/setup/commands).
* The `mypet-storage`-Citizens trait of [MyPet-NPC](https://wiki.mypet-plugin.de/hooks/npc).
* All pets obtained by ways other than taming them.

### How can I limit the amount of pets a player can store?

The amount of pets a player can store is limited by the following permission:

* `MyPet.petstorage.limit.X`
  * `X` needs to be replaced by the amount of pets a player should be able to store.
  * `X` needs to be smaller or equal than the `MyPet.Max-Stored-Pet-Count` in the [config.yml](../configuration/config.yml.md#max-stored-pet-count).

### What is the \`Max-Stored-Pet-Count\` config setting for?

Because the server needs to check a lot of permissions in order to check if the player is allowed to store more than his currently stored pets, this config setting jumps in and limits these checks.
