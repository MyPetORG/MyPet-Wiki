# Permissions

```yaml
  - MyPet.admin
  - MyPet.command.info.other
  - MyPet.command.capturehelper
  - MyPet.command.release
  - MyPet.command.respawn
  - MyPet.command.name
  - MyPet.command.name.color
  - MyPet.command.switch
  - MyPet.command.store
  - MyPet.command.trade.offer.<MyPet-Type>
  - MyPet.command.trade.receive.<MyPet-Type>
  - MyPet.shop.access.<shopname>
  - MyPet.shop.storage
  - MyPet.petstorage.limit.<limit>
  - MyPet.leash.<MyPet-Type>
  - MyPet.skilltree.<skilltreename>
  
  - MyPet.experience.multiplier.250
  - MyPet.experience.multiplier.225
  - MyPet.experience.multiplier.200
  - MyPet.experience.multiplier.175
  - MyPet.experience.multiplier.150
  - MyPet.experience.multiplier.125
  
  - MyPet.npc.storage
  - MyPet.npc.shop
```

## Leash Permissions

The leash permission is the most important permission because it allows to take a mob on a lead. You can allow all types by using the wildcard `*` or you can allow only certain types to certain players as you want. 

{% hint style="warning" %}
This permission only allows to leash a certain mob but everything else a player can do with a pet has nothing to do with this permission
{% endhint %}

* `MyPet.leash.<Pet-Type-Name>`
  * `<Pet-Type-Name>` has to be replaced with a valid Pet-Type-Name or wildcard\(`*`\) to give permission for all Pet-Types.
  * allows to leash a pet of this Pet-Type.

{% tabs %}
{% tab title="Wildcard \(\*\)" %}
```yaml
  - MyPet.leash.*
```
{% endtab %}

{% tab title="All" %}
```yaml
  - MyPet.leash.Bat
  - MyPet.leash.Blaze
  - MyPet.least.Cat
  - MyPet.leash.CaveSpider
  - MyPet.leash.Chicken
  - MyPet.leash.Cow
  - MyPet.leash.Creeper
  - MyPet.leash.Donkey
  - MyPet.leash.ElderGuardian
  - MyPet.leash.EnderDragon
  - MyPet.leash.Enderman
  - MyPet.leash.Endermite
  - MyPet.leash.Ghast
  - MyPet.leash.Giant
  - MyPet.leash.Guardian
  - MyPet.leash.Horse
  - MyPet.leash.Husk
  - MyPet.leash.Illusioner
  - MyPet.leash.IronGolem
  - MyPet.leash.Llama
  - MyPet.leash.MagmaCube
  - MyPet.leash.Mooshroom
  - MyPet.leash.Mule
  - MyPet.leash.Ocelot
  - MyPet.leash.Panda
  - MyPet.leash.Parrot
  - MyPet.leash.Pig
  - MyPet.leash.PigZombie
  - MyPet.leash.PolarBear
  - MyPet.leash.Rabbit
  - MyPet.leash.Sheep
  - MyPet.leash.Silverfish
  - MyPet.leash.Skeleton
  - MyPet.leash.SkeletonHorse
  - MyPet.leash.Slime
  - MyPet.leash.Snowman
  - MyPet.leash.Spider
  - MyPet.leash.Squid
  - MyPet.leash.Stray
  - MyPet.leash.Vex
  - MyPet.leash.Vindicator
  - MyPet.leash.Villager
  - MyPet.leash.Witch
  - MyPet.leash.Wither
  - MyPet.leash.WitherSkeleton
  - MyPet.leash.Wolf
  - MyPet.leash.Zombie
  - MyPet.leash.ZombieHorse
  - MyPet.leash.ZombieVillager
```
{% endtab %}
{% endtabs %}

## MyPet Permissions

* `MyPet.admin`
  * allows to:
    * open inventory of any pet.
    * open the inventory in creative mode/worlds.
    * switch skilltree as you want it.
    * access to _`/petadmin`_ command.
* `MyPet.command.info.other`
  * allows to view pet info of other players with the _`/petinfo`_ command.
* `MyPet.command.capturehelper`
  * allows to use the CaptureHelper.
* `MyPet.command.release`
  * allows to release your pet.
* `MyPet.command.name`
  * allows to rename your pet.
* `MyPet.command.name.color`
  * allows to use colors in pet-names.
* `MyPet.command.respawn`
  * allows to use the _`/petrespawn`_ command to respawn your pet \(needs Economy plugin\).
* `MyPet.command.switch`
  * allows to use the _`/petswitch`_ command to switch between pets.
* `MyPet.command.store`
  * allows to use the _`/petstore`_ command to store pets.
* `MyPet.command.trade.offer.<MyPet-Type>`
  * allows to offer somebody your MyPet of type `<MyPet-Type>`
* `MyPet.command.trade.receive.<MyPet-Type>`
  * allows to offer somebody your MyPet of type `<MyPet-Type>`
* `MyPet.petstorage.limit.<limit>`
  * limits the amount of pets a player can store.
  * `<limit>` has to be replaced by a number between 1 and 54
* `MyPet.shop.access.<shopname>`
  * allows to access a shop with the /petshop command
  * `<shopname>` needs to be replaced by a shop name
* `MyPet.shop.storage`
  * allows to buy pets to the storage so you don't have to store your pet before buying a new one
* `MyPet.skilltree.<skilltreename>`
  * `<skilltreename>` has to be replaced with the name of any existing skilltreename.
  * allows to use the `<skilltreename>` skilltree.
  * the names of the default skilltrees are: `Combat`, `Utility`, `PvP`, `Ride` & `Farm`
* `MyPet.npc.storage`
  * allows to interact with the `mypet-storage` Citizens trait
* `MyPet.npc.shop`
  * allows to interact with the `mypet-shop` Citizens trait
* `MyPet.experience.multiplier.`**`X`**
  * Allows the pets of this player to gain **`X`**% XP
  * For a full list of **`X`** see [list](permissions.md) at the top op this page

## Extended MyPet Permissions

To use the extended permissions you need to activate them in the config \(_`MyPet.Permissions.Extended`_\). Extended permissions are supposed to be used as a feature blocker. That means that it only usefull to active them when you want to disable certain features in certain worlds like disable Inventory in creative worlds. All these permissions should be self explaining but remember, they are only supposed to disable these things.

```yaml
  - MyPet.extended.feed
  - MyPet.extended.beacon
  - MyPet.extended.behavior.friendly
  - MyPet.extended.behavior.aggressive
  - MyPet.extended.behavior.farm
  - MyPet.extended.behavior.raid
  - MyPet.extended.behavior.duel
  - MyPet.extended.inventory
  - MyPet.extended.ride
  - MyPet.extended.ride.fly
  - MyPet.extended.control
  - MyPet.extended.pickup
  - MyPet.extended.equip
  - MyPet.extended.nametag
```

