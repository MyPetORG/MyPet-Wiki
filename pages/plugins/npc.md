# MyPet - NPC

**MyPet-NPC** is a simple addon for *MyPet* that adds a trait to Citizens that allows pet-owners to store their pets.

Every *WorldGroup* has it's own storage so you can not transfer pets between *WorldGroup*s.
You need **MyPet 1.1.1+** in order to use this plugin.

The Citizens **trait**s are called:

* `mypet-storage`  ->  MyPet Storage
* `mypet-wallet`  ->  Economy addon for the `mypet-storage` trait
* `mypet-shop`  ->  Pet shop

----

## Pictures

![Inventory](/wiki/images/plugins/npc/handover.png) ![Inventory](/wiki/images/plugins/npc/take.png)

----

## Commands


*  <font color="DarkCyan">/mypetnpcconfig wallet</font> <font color="LimeGreen">\[**Private**/**Owner**/**Bank**/**None**]</font>
    *  sets the account where the money will be transfered to
        *   Owner and Bank need a name as a 2nd parameter
    *  alias:
        * <font color="DarkCyan">/mpnpcc wallet</font>
<br>
* <font color="DarkCyan">/mypetnpcconfig shop</font> <font color="red">`<shop name>`</font>
    * set the shop that will be opened by the selected NPC
    * alias:
        * <font color="DarkCyan">/mpnpcc shop</font>

----

## Permissions

The `MyPet.petstorage.limit.<limit>` permission is shared with by <font color="DarkCyan">/petswitch store''</font> command and the **storage/shop trait**.
~~~
 - MyPet.npc.storage
 - MyPet.npc.shop

 - MyPet.petstorage.limit.<limit>
~~~

----

## Links

* Jenkins (download): [http://build.keyle.de/job/MyPet-NPC/](http://build.keyle.de/job/MyPet-NPC/)
* Source: [https://github.com/xXKeyleXx/MyPet-NPC](https://github.com/xXKeyleXx/MyPet-NPC)
* Report a problem: [https://github.com/xXKeyleXx/MyPet/issues](https://github.com/xXKeyleXx/MyPet/issues)
