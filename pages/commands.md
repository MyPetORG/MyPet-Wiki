# Commands

----
## Legend

*  <font color="DarkCyan">Chatcommands</font>
    * <font color="red">`<variable>`</font> -> required!
    * <font color="LimeGreen">[vaiable]</font> -> optional
Most commands have aliases like <font color="DarkCyan">/pi</font>. Use them instead the long version.

:!: In most cases you can also go through the command options by using the <kbd>TAB</kbd>-key. :!:


----

## MyPet Commands

----

*  <font color="DarkCyan">/mypet</font>
    * show all available *MyPet* commands.

----

*  <font color="DarkCyan">/petinfo </font><font color="LimeGreen">[username]</font>
    * show the following info about your or another player's pet.
        * hitpoints
        * experience
        * damage
        * owner (only when pets isn't yours)
        * skilltree
    * alias:
        * <font color="DarkCyan">/pinfo</font>

----

*  <font color="DarkCyan">/petname </font><font color="LimeGreen">[new-pet-name]</font>
    * set the name of your pet.
    * owners can use colors to make the name of their pets more colorfull with this placeholder:
        * `<black>`, `<darkblue>`, `<darkgreen>`, `<darkred>`, `<darkpurple>`, `<gold>`, `<gray>`, `<darkgray>`, `<blue>`, `<green>`, `<aqua>`, `<red>`, `<lightpurple>`, `<yellow>`, `<white>`, `<magic>`, `<bold>`, `<strikethrough>`, `<underline>`, `<italic>`, `<reset>`

----

*  <font color="DarkCyan">/petrelease </font><font color="LimeGreen">[pet-name]</font>
    * release your pet so you don't have a pet anymore

----

*  <font color="DarkCyan">/petcall</font>
    * teleports your pet to you.
    * alias:
        * <font color="DarkCyan">/pc</font>
        * <font color="DarkCyan">/petc</font>

----

*  <font color="DarkCyan">/petsendaway</font>
    * send your pet away.
    * it can be still called by using the <font color="green">/petcall</font> command
    * alias:
        * <font color="DarkCyan">/psa</font>
        * <font color="DarkCyan">/petsa</font>

----

*  <font color="DarkCyan">/petrespawn</font> <font color="LimeGreen">[**pay</font> or <font color="LimeGreen">show</font> or <font color="LimeGreen">auto**]</font>
    * show the following info about your or another player's pet.
        * <font color="LimeGreen">auto</font> with an addition parameter (Integer) determines what the maximum time is the player want to pay for
        * Example: A player used `/petrespawn auto 10` and the pet dies and has a respawn time of 16 seconds. Now the plugin will wait until the respawntime is 10 seconds and then respawn the pet when the owner can pay the respawn fee.
    * alias:
        * <font color="DarkCyan">/petr</font>
        * <font color="DarkCyan">/pr</font>

----

*  <font color="DarkCyan">/petswitch </font><font color="LimeGreen">[store]</font>
    * allows you to switch between pets or store your pet so you can catch a new one without losing the old one.
    * alias:
        * <font color="DarkCyan">/pswitch</font>

----

*  <font color="DarkCyan">/pettrade</font> <font color="red">[accept</font> or <font color="red">reject</font> or <font color="red">cancel</font> or a <font color="red">`<player name>`]</font> <font color="LimeGreen">`<price>`</font>
    * ![$](/wiki/images/premium.gif) only available in premium version
    * offers your current pet to another player.
        * <font color="LimeGreen">`<auto>`</font> can be any economy price
    * alias:
        * <font color="DarkCyan">/pett</font>
        * <font color="DarkCyan">/pt</font>

----

*  <font color="DarkCyan">/petskill </font><font color="LimeGreen">[playername]</font>
    * shows info about the skills of your pet.
    * as an admin this command you can also shows info about other player's pets

----

*  <font color="DarkCyan">/petadmin </font><font color="red">`<option>` </font><font color="LimeGreen">[parameters...]</font>
    * You need the *<font color="purple">MyPet.admin</font>* permission to use this command!
    * options:
        * <font color="red">name</font>
              * set the name of a pet for a specific player
              * parameters:
                  * <font color="LimeGreen">`<ownername>`</font>
                  * <font color="LimeGreen">`<new petname>`</font>
        * <font color="red">exp</font>
              * set the exp of a pet for a specific player
              * parameters:
                  * <font color="LimeGreen">`<ownername>`</font>
                  * <font color="LimeGreen">`<new exp of the pet>`</font>
                  * <font color="LimeGreen">[**add**/**set**/**remove**]</font>
        * <font color="red">respawn</font>
            * set/displays the respawnt time of a pet for a specific player
            * will only change the respawn time for dead pets
            * parameters:
                * <font color="LimeGreen">`<ownername>`</font>
                * <font color="LimeGreen">[new respawntime]</font> or <font color="LimeGreen">[**show**]</font>
        * <font color="red">reload</font>
            * reloads the config file (config.yml) and translations
        * <font color="red">reloadskills</font>
            * reloads the skilltrees
        * <font color="red">skilltree</font>
            * changes the skilltree of a pet
            * parameters:
                * <font color="LimeGreen">`<pet ownername>`</font>
                * <font color="LimeGreen">`<skilltree>`</font>
        * <font color="red">build</font>
            * shows the *MyPet* version and build number
        * <font color="red">create</font>
            * creates a new pet for a specific player
            * not usable when player has an active pet
            * use <font color="LimeGreen">-f</font> to create a new pet even if the player has a pet already
            * parameters:
                * <font color="LimeGreen">[**-f**]</font>
                * <font color="LimeGreen">`<ownername>`</font>
                * <font color="LimeGreen">`<pettype>`</font>
                * <font color="LimeGreen">[parameter]</font>
            * Use the <kbd>TAB</kbd>-key to see all possible paramerters for the selected pettype
        * <font color="red">clone</font>
            * clones a pet from a player and gives it to another player
            * parameters:
                * <font color="LimeGreen">`<pet ownername>`</font>
                * <font color="LimeGreen">`<new pet ownername>`</font>
        * <font color="red">remove</font>
            * deletes a pet of a specific player
            * parameters:
                * <font color="LimeGreen">`<ownername>`</font>
        * <font color="red">cleanup</font>
            * deletes unused pets older than a certain amount of time
            * if no parameter is given all pets which aren't used after the upgrade to MyPet 1.1.3
            * parameters (example):
                * <font color="LimeGreen">[1Y] [1D] [1H] [1M]</font>
        * <font color="red">ticket</font>
            * creates a ZIP file that contains all the info the developers need when you ask something on [GitHub](https://github.com/xXKeyleXx/MyPet/issues)

----

*  <font color="DarkCyan">/petstop</font>
    * orders your pet to stop attacking his target
    * useless in `farm` and `aggressive` behavior modes
    * alias:
      * <font color="DarkCyan">/ps</font>
      * <font color="DarkCyan">/pets</font>

----

*  <font color="DarkCyan">/petskilltree </font><font color="red">`<mobtype>` </font><font color="LimeGreen">[skilltree name]</font>
    * shows all available skilltrees for a mobtype
    * shows all levels and skills for a skilltree of a mobtype
    * ** :!: can only be used in the server console :!: **

----

*  <font color="DarkCyan">/petchooseskilltree </font><font color="LimeGreen">[skilltree name]</font>
    * shows all available skilltrees and lets you selects a skilltree for your pet
    * since MyPet 1.1.3 this command will bring up an item menu for the skilltree selection (Spoiler below)
    * alias:
      * <font color="DarkCyan">/pcst</font>
      * <font color="DarkCyan">/petcst</font>

![PCST](/wiki/images/pcst.png)

----

*  <font color="DarkCyan">/petcapturehelper </font>
    * enable/disable the CaptureHelper
    * alias:
      * <font color="DarkCyan">/pch</font>

----

*  <font color="DarkCyan">/pettype </font><font color="red">`<pettype>`</font>
    * displays info about the pettype like `default HP`, `leash flags` and `food`

----

*  <font color="DarkCyan">/petoptions </font><font color="red">`<option>` </font><font color="LimeGreen">[parameters...]</font>
    * options:
        * <font color="red">healthbar</font>
            * toggles healthbar on/off
        * <font color="red">idle-volume</font>
            * set the volume of the idle sound pets make
            * parameters:
                * <font color="LimeGreen">`<percent>`</font>


----

## Skill Commands

----

*  <font color="DarkCyan">/petinventory</font> <font color="LimeGreen">[playername]</font>
    * opens the inventory of your pet
    * can not be opened when pet is in water/lava
    * opening the inventory of another player requires the *<font color="purple">MyPet.admin</font>* permission
    * alias:
        * <font color="DarkCyan">/pi</font>
        * <font color="DarkCyan">/peti</font>

----

*  <font color="DarkCyan">/petpickup</font>
    * toggles pickup of your pet on/off
    * :!: requires <font color="blue">Inventory</font> with at least one row of slots :!:
    * alias:
      * <font color="DarkCyan">/pp</font>
      * <font color="DarkCyan">/petp</font>

----

*  <font color="DarkCyan">/petbehavior </font><font color="LimeGreen">[mode]</font>
    * toggles the behavior your pet
    * modes:
        * <font color="LimeGreen">friendly</font> -> the pet will not fight even when it's attacked by anything
            * friend
        * <font color="LimeGreen">normal</font> -> the pet will act like a normal wolf
        * aggressive -> attacks automaticly everythink within 15 blocks of the owner
            * aggro
        * <font color="LimeGreen">farm</font> -> attacks automaticly every **Monster** within 15 blocks of the owner
        * <font color="LimeGreen">raid</font> -> like <font color="LimeGreen">normal</font> but the pet will not attack players and their minions (wolves, ocelot, pets)
        * <font color="LimeGreen">duel</font> -> pets will attack other pets with active duel behavior within a 5 block radius
    * alias:
        * <font color="DarkCyan">/pb</font>
        * <font color="DarkCyan">/petb</font>

----

*  <font color="DarkCyan">/petbeacon</font>
    * opens the beacon window of your pet
    * alias:
        * <font color="DarkCyan">/pbeacon</font>
        * <font color="DarkCyan">/petbeacon</font>
