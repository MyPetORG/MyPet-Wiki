# MyPet - MultiWorld

**MyPet-MultiWorld** is a simple addon for *MyPet* that provides multiworld support.
Every world is in a *WorldGroup* and every player can have one *MyPet* per *WorldGroup*, so players can have multiple pets on one server.
The *MyPet* will switch automatically when the player changes the world and enters another *WorldGroup*.

## Download

Temporary Download Link: [MyPet-MultiWorld-0.0.1-SNAPSHOT.jar](http://build.keyle.de/job/MyPet-MultiWorld/lastSuccessfulBuild/artifact/target/MyPet-MultiWorld-0.0.1-SNAPSHOT.jar) <br>
Jenkins: [MyPet-MultiWorld](http://build.keyle.de/job/MyPet-MultiWorld/)

## Installation

Just put the  plugin-`jar`-file into the plugins folder and start the server.<br>
The plugin will create the a default *WorldGroup* configuration and adds all worlds to the `default` *WorldGroup*.

## Configuration

Every world has to be in a *WorldGroup*. You can create as much *WorldGroups* as you want as long as every world is in only **one** *WorldGroup*.<br>

Example configuration: (All players will have a *MyPet* in the normal worlds an one in the nether worlds)
`<code|yaml>`Groups:
    default:
 1.  normal
 2.  2ndWorld
    nether:
 3.  normal_nether
 4.  2ndWorld_nether
`</code>`
