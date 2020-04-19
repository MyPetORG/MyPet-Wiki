# World Groups

To allows server owners to manage the worlds where players have the same pet, MyPet uses World-groups to combine different worlds together \(or split them up\). These groups are managed in the `worldgroups.yml` file.

Changes made to the `worldgroups.yml` file will require a complete server restart. The reload command will not enforce these changes.

## How does it work?

Every world is in a _World-group_ and every player can have one active pet per _World-group_, so players can have multiple pets on one server. The pet will switch automatically when the player changes the world and enters another _World-group_.

## How can I disable pets in certain worlds?

Put the world\(s\) into a new world-group \(you can all the group whatever you want, for example `nopets`\). Then remove \(or don't add\) the leash [permissions](../setup/permissions.md) form these worlds. Now no new pets can be created an no pets can enter this world.

## Installation

The plugin will create the default _World-group_ configuration file and adds every available world to the `default` _World-group_.

## Configuration

Every world has to be in a _World-group_. You can create as many _World-groups_ as you want as long as every world is in just **one** _World-group_.

**Example configuration:** With this configuration every player can have one pet in the normal worlds and one in the nether worlds

```text
Groups:
  default:
  - normal
  - 2ndWorld
  nether:
  - normal_nether
  - 2ndWorld_nether
```

## Disable Worlds

You can also disable world where MyPet will not be active. This world cannot be in a world group.The config is also in the worldgroups.yml:

```text
Disabled:
- example_world
```

