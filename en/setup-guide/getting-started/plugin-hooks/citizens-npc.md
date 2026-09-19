---
icon: person
---

# Citizens NPC

A MyPet feature adding a trait to Citizens that allows pet-owners to store their pets.

Every [world group](../systems/world-groups.md) has its own storage so you cannot transfer pets between world groups.

The Citizens traits are called:

* `mypet-storage` -> MyPet Storage
* `mypet-wallet` -> Economy function for the `mypet-storage` trait
* `mypet-shop` -> Pet shop

{% columns fullWidth="true" %}
{% column %}
![](../../.gitbook/assets/image)
{% endcolumn %}

{% column %}
![](<../../.gitbook/assets/image (1)>)
{% endcolumn %}
{% endcolumns %}

### Commands

For all NPC commands you need to select a Citizens NPC first!

* `/petadmin npc wallet [Private/Owner/Bank/None]`
  * sets the account where the money will be transferred to
  * Owner and Bank need a name as a 2nd parameter
* `/petadmin npc shop`
  * set the shop that will be opened by the selected NPC

### Permissions

The limit afforded by the `MyPet.petstorage.limit.<limit>` permission is shared by both `/petstore` command usage and the storage/shop trait.

* `MyPet.npc.storage`
* `MyPet.npc.shop`
* `MyPet.petstorage.limit.<limit>`
