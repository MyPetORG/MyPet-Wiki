# MyPet - NPC

**MyPet-NPC** is a simple addon for *MyPet* that adds a trait to Citizens that allows *MyPet*-owners to store their MyPets.<br>
<br>
Every *WorldGroup* has it's own storage so you can not transfer *MyPet*s between *WorldGroup*s.<br>
You need **MyPet 1.1.1+** in order to use this plugin.<br>
<br>
The Citizens **trait**s are called:

* `mypet-storage`  ->  MyPet Storage
* `mypet-wallet`  ->  Wallet (Economy)

----

## Links

Jenkins (download): [MyPet-NPC](http://build.keyle.de/job/MyPet-NPC/) <br>
Source: https://github.com/xXKeyleXx/MyPet-NPC <br>
BugReport: https://github.com/xXKeyleXx/MyPet/issues <br>

----

## Pictures

![Inventory](/wiki/images/plugins/npc/handover.png)
![Inventory](/wiki/images/plugins/npc/take.png)

----

## Commands


*  <font color="DarkCyan">/mypetnpcconfig wallet</font> <font color="LimeGreen">[**Private**/**Owner**/**Bank**/**None**]</font>
    *  sets the account where the money will be transfered to
        *   Owner and Bank need a name as a 2nd parameter
    *  alias:
        *   <font color="DarkCyan">/mpnpcc</font>

## Permissions

`MyPet.npc.storage.max.<size>` determines how many pets can be stored.
~~~
 - MyPet.npc.storage
 - MyPet.npc.storage.bypass

 - MyPet.npc.storage.max.54
           ...
 - MyPet.npc.storage.max.1
~~~
