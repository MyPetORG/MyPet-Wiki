---
icon: people-roof
---

# World Groups

To allow server owners to manage the worlds where players have the same pet, MyPet uses World-groups to combine different worlds together (or split them up). These groups are managed in the `worldgroups.yml` file.

Changes made to the `worldgroups.yml` file will require a complete server restart. The reload command will not enforce these changes.

### How does it work?

Every world is in a _World-group_ and every player can have one active pet per _World-group_, so players can have multiple sets of pets on one server. The pet will switch automatically when the player changes the world and enters another _World-group_.

### How can I disable pets in certain worlds?

There are two methods you could use to disable pets in specific worlds:

* The simplest method is to include worlds under a `Disabled:` key in `worldgroups.yml`, as shown [below](world-groups.md#disable-worlds).
* You can also put the world(s) into a new world-group (you can call the group whatever you want, for example `nopets`). Then remove (or don't add) the leash [permissions](https://wiki.mypet-plugin.de/setup/permissions) from these worlds. Now no new pets can be created and no pets can enter this world.

### Installation

The plugin will create the default `worldgroups.yml` configuration file and add every available world to the `default` _World-group_.

### Configuration

Every world has to be in a _World-group_. You can create as many _World-groups_ as you want as long as every world is in just **one** _World-group_.

Example configuration: With this configuration every player can have one pet in the normal worlds and one in the nether worlds.

{% code title="worldgroups.yml" %}
```yaml
Groups:
  default:
  - normal
  - 2ndWorld
  nether:
  - normal_nether
  - 2ndWorld_nether
Disabled:
- example_world
```
{% endcode %}

### Disable Worlds

You can specify worlds where MyPet will not be active. Using the `Disabled:` key in `worldgroups.yml` you can list any worlds that should be disabled. These worlds should not also be included in any other world-group.&#x20;

Example:

{% code title="worldgroups.yml" %}
```yaml
Disabled:
- example_world
```
{% endcode %}
