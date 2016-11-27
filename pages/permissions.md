# MyPet - Permissions

**Normal Permissions:**
~~~
  - MyPet.admin
  - MyPet.command.info.other
  - MyPet.command.capturehelper
  - MyPet.command.release
  - MyPet.command.respawn
  - MyPet.command.name
  - MyPet.command.name.color
  - MyPet.command.switch
  - MyPet.command.options.resourcepack
  - MyPet.command.trade.offer.<MyPet-Type>
  - MyPet.command.trade.receive.<MyPet-Type>
  - MyPet.shop.access.<shopname>
  - MyPet.petstorage.limit.<limit>
  - MyPet.leash.<MyPet-Type>
  - MyPet.skilltree.<skilltreename>
~~~
----
## MyPet Leash Permissions

The leash permission is the most important permission because it allows to take a mob on a lead.
You can allow all types by using the wildcard `*` or you can allow only certain types to certain players as you want.
![$](/wiki/images/exclaim.gif) This permission only allows to leash a certain mob but everything else a player can do with a pet has nothing to do with this permission ![$](/wiki/images/exclaim.gif)

* `MyPet.leash.<Pet-Type-Name>`
  * `<Pet-Type-Name>` has to be replaced with a valid Pet-Type-Name or wildcard(`*`) to give permission for all Pet-Types.
  * allows to leash a pet of this Pet-Type.

~~~
  - MyPet.leash.*
~~~
or
~~~
  - MyPet.leash.Bat
  - MyPet.leash.Blaze
  - MyPet.leash.CaveSpider
  - MyPet.leash.Chicken
  - MyPet.leash.Cow
  - MyPet.leash.Creeper
  - MyPet.leash.EnderDragon
  - MyPet.leash.Enderman
  - MyPet.leash.Endermite
  - MyPet.leash.Ghast
  - MyPet.leash.Giant
  - MyPet.leash.Guardian
  - MyPet.leash.IronGolem
  - MyPet.leash.MagmaCube
  - MyPet.leash.Mooshroom
  - MyPet.leash.Ocelot
  - MyPet.leash.Pig
  - MyPet.leash.PigZombie
  - MyPet.leash.PolarBear
  - MyPet.leash.Rabbit
  - MyPet.leash.Sheep
  - MyPet.leash.Silverfish
  - MyPet.leash.Skeleton
  - MyPet.leash.Slime
  - MyPet.leash.Snowman
  - MyPet.leash.Spider
  - MyPet.leash.Villager
  - MyPet.leash.Witch
  - MyPet.leash.Wither
  - MyPet.leash.Wolf
  - MyPet.leash.Zombie
~~~

----
## Other MyPet Permissions

*  `MyPet.admin`
    * allows to:
        * open inventory of any pet.
        * open the inventory in creative mode/worlds.
        * switch skilltree as you want it.
        * access to <font color="DarkCyan">_/petadmin_</font> command.
*  `MyPet.command.info.other`
     * allows to view pet info of other players with the <font color="DarkCyan">_/petinfo_</font> command.
*  `MyPet.command.capturehelper`
     * allows to use the CaptureHelper.
*  `MyPet.command.release`
     * allows to release your pet.
*  `MyPet.command.name`
     * allows to rename your pet.
*  `MyPet.command.name.color`
     * allows to use colors in pet-names.
*  `MyPet.command.respawn`
     * allows to use the <font color="DarkCyan">/petrespawn</font> command to respawn your pet (needs Economy plugin).
*  `MyPet.command.switch`
     * allows to use the <font color="DarkCyan">/petswitch</font> command to switch between pets.
*  `MyPet.command.options.resourcepack`
     * allows to use the <font color="DarkCyan">/petoptions resource-pack</font> command to toggle the resource pack.
*  `MyPet.command.trade.offer.<MyPet-Type>`
     * allows to offer somebody your MyPet of type `<MyPet-Type>`
     * ![$](/wiki/images/premium.gif) Premium feature
*  `MyPet.command.trade.receive.<MyPet-Type>`
     * allows to offer somebody your MyPet of type `<MyPet-Type>`
     * ![$](/wiki/images/premium.gif) Premium feature
*  `MyPet.petstorage.limit.<limit>`
     * limits the amount of pets a player can store.
     * `<limit>` has to be replaced by a number between 1 and 54
* `MyPet.shop.access.<shopname>`
     * allows to access a shop with the <font color="DarkCyan">/petshop <shopname></font> command
     * `<shopname>` needs to be replaced by a shop name
     * ![$](/wiki/images/premium.gif) Premium feature
*  `MyPet.skilltree.<skilltreename>`
     * `<skilltreename>` has to be replaced with the name of any existing skilltreename.
     * allows to use the `<skilltreename>` skilltree.
     * ![$](/wiki/images/exclaim.gif) you can't use `MyPet.skilltree.*` with GroupManager (Essentials) ![$](/wiki/images/exclaim.gif)
     * the names of the default skilltrees are: **`Combat`**, **`Utility`**, **`PvP`**, **`Ride`** & **`Farm`**

----
## Extended MyPet Permissions

To use the extended permissions you need to activate them in the config (<font color="Coral">_MyPet.Permissions.Extended_</font>)
Extended permissions are supposed to be used as a feature blocker. That means that it only usefull to active them when you want to disable certain features in certain worlds like disable Inventory in creative worlds.
All these permissions should be self explaining but remember, they are only supposed to disable these things.
~~~
  - MyPet.extended.feed
  - MyPet.extended.beacon
  - MyPet.extended.behavior.friendly
  - MyPet.extended.behavior.aggressive
  - MyPet.extended.behavior.farm
  - MyPet.extended.behavior.raid
  - MyPet.extended.behavior.duel
  - MyPet.extended.inventory
  - MyPet.extended.ride
  - MyPet.extended.control
  - MyPet.extended.pickup
  - MyPet.extended.equip
  - MyPet.extended.nametag
~~~
