# MyPet Storage

The MyPet storage is way to have more than one MyPet. This doesn't mean you can have more than one pet active at a time but to store any pets you don't want active at the set moment.

## What uses the storage?

* The pet [shop](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/pages/shop/README.md)
* the /petstore and /petswitch [commands](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/pages/commands/README.md)
* The `mypet-storage`-Citizens trait of [MyPet-NPC](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/pages/plugins/npc/README.md)
* all pets obtained by other sources than taming them

## How can I limit the amount of pets a player can store?

The amount of pets a player can store is limited by the following permission:

* \_MyPet.petstorage.limit.\\_
* \ needs to be replaced by the amount a player should be allowed to store.

## What is the Max-Stored-Pet-Count config setting for?

Because the server needs to check a lot of permissions in order to check if the player is allowed to store more than his currently stored pets, there is a config setting that limits these checks.

