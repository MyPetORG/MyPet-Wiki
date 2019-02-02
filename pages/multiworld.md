# World Groups

To allows server owners to manage the worlds where players have the same pet, MyPet uses WorlGroups to combine different worlds together \(or split them up\). These groups are managed in the `worldgroups.yml` file.

## How does it work?

Every world is in a _WorldGroup_ and every player can have one pet per _WorldGroup_, so players can have multiple pets on one server. The pet will switch automatically when the player changes the world and enters another _WorldGroup_.

## How can I disable pets in certain worlds?

Put the world\(s\) into a new worldgroup \(you can all the group whatever you want, for example `nopets`\). Then remove \(or don't add\) the leash [permissions](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/pages/permissions/README.md#mypet_leash_permissions) form these worlds. Now no new pets can be created an no pets can enter this world.

## Installation

The plugin will create the a default _WorldGroup_ configuration file and adds every available world to the `default` _WorldGroup_.

## Configuration

Every world has to be in a _WorldGroup_. You can create as much _WorldGroups_ as you want as long as every world is in just **one** _WorldGroup_.

Example configuration: With this configuration every player can have one pet in the normal worlds an one in the nether worlds

```text
Groups:
  default:
  - normal
  - 2ndWorld
  nether:
  - normal_nether
  - 2ndWorld_nether
```

