# MyPet - NPC

**MyPet-NPC** is a simple addon for *MyPet* that adds a trait to Citizens that allows *MyPet*-owners to store their MyPets.\\
\\
Every *WorldGroup* has it's own storage so you can not transfer *MyPet*s between *WorldGroup*s.\\
You need **MyPet 1.1.1+** in order to use this plugin.\\
\\
The Citizens **trait**s are called:

*  ''mypet-storage''  ->  MyPet Storage

*  ''mypet-wallet''  ->  Wallet (Economy)

----

## Links

Jenkins (download): [MyPet-NPC](http://build.keyle.de/job/MyPet-NPC/) \\
Source: https://github.com/xXKeyleXx/MyPet-NPC \\
BugReport: https://github.com/xXKeyleXx/MyPet/issues \\
----

## Pictures

{{:images:plugins:npc:handover.png?400|}}{{:images:plugins:npc:take.png?400|}}

----

## Commands


*  `<color DarkCyan>`/mypetnpcconfig wallet`</color>` `<color LimeGreen>`[**Private**/**Owner**/**Bank**/**None**]`</color>`
    * sets the account where the money will be transfered to
      * Owner and Bank need a name as a 2nd parameter
    * alias:
      * `<color DarkCyan>`/mpnpcc`</color>`

## Permissions

''MyPet.npc.storage.max.`<size>` determines how many *MyPet*s can be stored.
`<code|yaml>` - MyPet.npc.storage
 - MyPet.npc.storage.bypass

 - MyPet.npc.storage.max.54
           ...
 - MyPet.npc.storage.max.1
`</code>`

----


