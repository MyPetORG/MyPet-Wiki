# Commands

----
## Legend

*  `<color DarkCyan>`Chatcommands`</color>`\\
    * `<color red>``<variable>``</color>` -> required!\\
    * `<color LimeGreen>`[vaiable]`</color>` -> optional\\
Most commands have aliases like `<color DarkCyan>`/pi`</color>`. Use them instead the long version.\\

:!: In most cases you can also go through the command options by using the `<key>`TAB`</key>`-key. :!:


----

## MyPet Commands

----

*  `<color DarkCyan>`/mypet`</color>`
    * show all available *MyPet* commands.

----


*  `<color DarkCyan>`/petinfo `</color>``<color LimeGreen>`[username]`</color>`
    * show the following info about your or another player's *MyPet*.
      * hitpoints
      * experience
      * damage
      * owner (only when *MyPet*s isn't yours)
      * skilltree
    * alias:
      * `<color DarkCyan>`/pinfo`</color>`

----


*  `<color DarkCyan>`/petname `</color>``<color LimeGreen>`[new-pet-name]`</color>`
    * set the name of your *MyPet*.
    * owners can use colors to make the name of their pets more colorfull with this placeholder:
      * `<black>`, `<darkblue>`, `<darkgreen>`, `<darkred>`, `<darkpurple>`, `<gold>`, `<gray>`, `<darkgray>`, `<blue>`, `<green>`, `<aqua>`, `<red>`, `<lightpurple>`, `<yellow>`, `<white>`, `<magic>`, `<bold>`, `<strikethrough>`, `<underline>`, `<italic>`, `<reset>`

----


*  `<color DarkCyan>`/petrelease `</color>``<color LimeGreen>`[pet-name]`</color>`
    * release your *MyPet* so you don't have a *MyPet* anymore

----


*  `<color DarkCyan>`/petcall`</color>`
    * teleports your *MyPet* to you.
    * alias:
      * `<color DarkCyan>`/pc`</color>`
      * `<color DarkCyan>`/petc`</color>`

----


*  `<color DarkCyan>`/petsendaway`</color>`
    * send your *MyPet* away.
    * it can be still called by using the `<color green>`/petcall`</color>` command
    * alias:
      * `<color DarkCyan>`/psa`</color>`
      * `<color DarkCyan>`/petsa`</color>`

----


*  `<color DarkCyan>`/petrespawn`</color>` `<color LimeGreen>`[**pay`</color>` or `<color LimeGreen>`show`</color>` or `<color LimeGreen>`auto**]`</color>`
    * show the following info about your or another player's *MyPet*.
      * `<color LimeGreen>`auto`</color>` with an addition parameter (Integer) determines what the maximum time is the player want to pay for
        * Example: A player used ''/petrespawn auto 10'' and the pet dies and has a respawn time of 16 seconds. Now the plugin will wait until the respawntime is 10 seconds and then respawn the pet when the owner can pay the respawn fee.
    * alias:
      * `<color DarkCyan>`/petr`</color>`
      * `<color DarkCyan>`/pr`</color>`

----


*  `<color DarkCyan>`/petswitch `</color>``<color LimeGreen>`[store]`</color>`
    * allows you to switch between MyPets or store your MyPet so you can catch a new one without losing the old one.
    * alias:
      * `<color DarkCyan>`/pswitch`</color>`

----


*  `<color DarkCyan>`/pettrade`</color>` `<color red>`[accept`</color>` or `<color red>`reject`</color>` or `<color red>`cancel`</color>` or a `<color red>``<player name>`]`</color>` `<color LimeGreen>``<price>``</color>`
    * (P) only available in premium version
    * offers your current *MyPet* to another player.
      * `<color LimeGreen>``<auto>``</color>` can be any economy price
    * alias:
      * `<color DarkCyan>`/pett`</color>`
      * `<color DarkCyan>`/pt`</color>`

----


*  `<color DarkCyan>`/petskill `</color>``<color LimeGreen>`[playername]`</color>`
    * shows info about the skills of your *MyPet*.
    * as an admin this command you can also shows info about other player's *MyPet*s

----


*  `<color DarkCyan>`/petadmin `</color>``<color red>``<option>` `</color>``<color LimeGreen>`[parameters...]`</color>`
    * You need the *`<color purple>`MyPet.admin`</color>`* permission to use this command!
    * options:
      * `<color red>`name`</color>`
        * set the name of a *MyPet* for a specific player
        * parameters:
          * `<color LimeGreen>``<ownername>``</color>`
          * `<color LimeGreen>``<new petname>``</color>`
      * `<color red>`exp`</color>`
        * set the exp of a *MyPet* for a specific player
        * parameters:
          * `<color LimeGreen>``<ownername>``</color>`
          * `<color LimeGreen>``<new exp of the pet>``</color>`
          * `<color LimeGreen>`[**add**/**set**/**remove**]`</color>`
      * `<color red>`respawn`</color>`
        * set/displays the respawnt time of a *MyPet* for a specific player
        * will only change the respawn time for dead *MyPet*s
        * parameters:
          * `<color LimeGreen>``<ownername>``</color>`
          * `<color LimeGreen>`[new respawntime]`</color>` or `<color LimeGreen>`[**show**]`</color>`
      * `<color red>`reload`</color>`
        * reloads the config file (config.yml)
      * `<color red>`reloadskills`</color>`
        * reloads the skilltrees
      * `<color red>`skilltree`</color>`
        * changes the skilltree of a *MyPet*
        * parameters:
          * `<color LimeGreen>``<pet ownername>``</color>`
          * `<color LimeGreen>``<skilltree>``</color>`
      * `<color red>`build`</color>`
        * shows *MyPet* version and buildnumber
      * `<color red>`create`</color>`
        * creates a new *MyPet* for a specific player
        * Only usable when player has no active *MyPet*
        * Use `<color LimeGreen>`-f`</color>` to create a new pet even if the player has a pet already
        * parameters:
          * `<color LimeGreen>`[**-f**]`</color>`
          * `<color LimeGreen>``<ownername>``</color>`
          * `<color LimeGreen>``<pettype>``</color>`
          * `<color LimeGreen>`[parameter]`</color>`
            * Use the `<key>`TAB`</key>`-key to see all possible paramerters for the selected pettype
      * `<color red>`clone`</color>`
        * clones a *MyPet* from a player and gives it to another player
        * parameters:
          * `<color LimeGreen>``<pet ownername>``</color>`
          * `<color LimeGreen>``<new pet ownername>``</color>`
      * `<color red>`remove`</color>`
        * deletes a new *MyPet* for a specific player
        * parameters:
          * `<color LimeGreen>``<ownername>``</color>`
      * `<color red>`cleanup`</color>`
        * deletes unused pets older than a certain amount of time
        * if no parameter is given all pets which aren't used after the upgrade to MyPet 1.1.3
        * parameters (example):
          * `<color LimeGreen>`[1Y] [1D] [1H] [1M]`</color>`
      * `<color red>`ticket`</color>`
        * creates a ZIP file that contains all the info the developers need when you ask something on [GitHub](https///github.com/xXKeyleXx/MyPet/issues)

----


*  `<color DarkCyan>`/petstop`</color>`
    * your *MyPet* stop attacking his taget
    * useless in ''farm'' and ''aggressive'' behavior modes
    * alias:
      * `<color DarkCyan>`/ps`</color>`
      * `<color DarkCyan>`/pets`</color>`



----


*  `<color DarkCyan>`/petskilltree `</color>``<color red>``<mobtype>` `</color>``<color LimeGreen>`[skilltree name]`</color>`
    * shows all available skilltrees for a choosen mobtype.
    * shows all level and skills for a choosen skilltree of a choosen mobtype
    * ** :!: can only be used in the server console :!: **

----


*  `<color DarkCyan>`/petchooseskilltree `</color>``<color LimeGreen>`[skilltree name]`</color>`
    * shows all available skilltrees.
    * selects a skilltree for your *MyPet*.
    * since MyPet 1.1.3 this command will bring up an item menu for the skilltree selection (Spoiler below)
    * alias:
      * `<color DarkCyan>`/pcst`</color>`
      * `<color DarkCyan>`/petcst`</color>`

`<spoiler=ItemMenu>`{{ :images:pcst.png?nolink |}}`</spoiler>`

----


*  `<color DarkCyan>`/petcapturehelper `</color>` 
    * enable/disable CaptureHelper
    * alias:
      * `<color DarkCyan>`/pch`</color>`

----


*  `<color DarkCyan>`/pettype `</color>``<color red>``<pettype>``</color>` 
    * displays info about the pettype like ''default HP'', ''leash flags'' and ''food''

----


*  `<color DarkCyan>`/petoptions `</color>``<color red>``<option>` `</color>``<color LimeGreen>`[parameters...]`</color>`
    * options:
      * `<color red>`healthbar`</color>`
        * toggles healthbar on/off
      * `<color red>`idle-volume`</color>`
        * set the volume of the idle sound *MyPet*s make
        * parameters:
          * `<color LimeGreen>``<percent>``</color>`


----
## Skill Commands

----


*  `<color DarkCyan>`/petinventory`</color>` `<color LimeGreen>`[playername]`</color>`
    *opens the inventory of your *MyPet*.
    *can not be opened when pet is in water/lava
    *opening the inventory of another player requires the *`<color purple>`MyPet.admin`</color>`* permission
    *alias:
      * `<color DarkCyan>`/pi`</color>`
      * `<color DarkCyan>`/peti`</color>`

----


*  `<color DarkCyan>`/petpickup`</color>`
    * toggles pickup of your *MyPet* on/off
    * :!: requires `<color blue>`Inventory`</color>` with at least one row of slots :!:
    * alias:
      * `<color DarkCyan>`/pp`</color>`
      * `<color DarkCyan>`/petp`</color>`

----


*  `<color DarkCyan>`/petbehavior `</color>``<color LimeGreen>`[mode]`</color>`
    * toggles the behavior your *MyPet*.
    * Modes:
      * `<color LimeGreen>`friendly`</color>` -> the *MyPet* will not fight even when it's attacked by anything
        * friend
      * `<color LimeGreen>`normal`</color>` -> the *MyPet* will act like a normal wolf
      * aggressive -> attacks automaticly everythink within 15 blocks of the owner
        * aggro
      * `<color LimeGreen>`farm`</color>` -> attacks automaticly every **Monster** within 15 blocks of the owner
      * `<color LimeGreen>`raid`</color>` -> like `<color LimeGreen>`normal`</color>` but the *MyPet* will not attack players and their minions (wolves, ocelot, *MyPet*s)
      * `<color LimeGreen>`duel`</color>` -> pets will attack other pets with active duel behavior within a 5 block radius
    * alias:
      * `<color DarkCyan>`/pb`</color>`
      * `<color DarkCyan>`/petb`</color>`

----


*  `<color DarkCyan>`/petbeacon`</color>`
    *opens the beacon window of your *MyPet*.
    *alias:
      * `<color DarkCyan>`/pbeacon`</color>`
      * `<color DarkCyan>`/petbeacon`</color>`
