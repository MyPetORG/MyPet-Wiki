---
description: Pet Configuration
---

# pet-config.yml

The _`pet-config.yml`_ file contains all MyPet-Type specific settings. All other settings can be found in the main config ([config.yml](config.yml.md)).

| Setting                        | Type   | Description                                                                                                                  |
| ------------------------------ | ------ | ---------------------------------------------------------------------------------------------------------------------------- |
| MyPet:                         |        |                                                                                                                              |
|   Pets:                        |        |                                                                                                                              |
|     \<MyPet-Type-Name>:        |        |                                                                                                                              |
|       HP:                      | double | The maximum HP the pet (type) has by default.                                                                                |
|       Speed:                   | double | <p>The running speed the pet-type has by default.</p><p>❗ Small changes have a massive impact on the speed ❗</p>             |
|       Food:                    | list   | The food this pet-type eats. This setting must be a list of valid [config items](configitems.md)                             |
|       LeashItem:               | string | The item this pet-type can be leashed with. This setting must be a valid [config item](configitems.md)                       |
|       LeashRequirements:       | list   | A list of valid [Leash Requirements](../../systems/leashflag.md)                                                             |
|       CustomRespawnTimeFactor: | int    | This setting allows to change the respawn times pet-type. This value will be added on top of the value from the main config. |
|       CustomRespawnTimeFixed:  | int    | This setting allows to change the respawn times pet-type. This value will be added on top of the value from the main config. |
|       ReleaseOnDeath:          | bool   | Whether or not the pet is released on death.                                                                                 |
|       RemoveAfterRelease:      | bool   | Whether or not the Mob is deleted after the pet is released.                                                                 |
