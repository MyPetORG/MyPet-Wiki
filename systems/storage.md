---
description: The MyPet storage is way to have more than one MyPet.
---

# MyPet Storage

This doesn't mean you can have more than one pet active at a time but to store any pets you don't want active at the set moment.

## What uses the storage?

* The pet [shop](../premium.md)
* the `/petstore` and `/petswitch` [commands](../setup/commands.md)
* The `mypet-storage`-Citizens trait of [MyPet-NPC](../hooks/npc.md)
* all pets obtained by other sources than taming them

## How can I limit the amount of pets a player can store?

The amount of pets a player can store is limited by the following permission:

* `MyPet.petstorage.limit.`**`X`**
* **`X`** needs to be replaced by the amount of pets a player should be able to store.

## What is the Max-Stored-Pet-Count config setting for?

Because the server needs to check a lot of permissions in order to check if the player is allowed to store more than his currently stored pets, there is a config setting that limits these checks.

