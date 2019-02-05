---
description: Pet Configuration
---

# pet-config.yml

The _pet-config.yml_ file contains all MyPet-Type specific settings. All other settings can be found in the main config \([config.yml](configfile.md)\).

| Setting | Type | Description |
| :--- | :---: | ---: |
| **MyPet:** |  |  |
|   **Pets:** |  |  |
| These settings are per MyPet-Type |  |  |
|     **&lt;MyPet-Type-Name&gt;:** |  |  |
|       HP: | double | The maximum HP the pet \(type\) has by default. |
|       Speed: | double | The running speed the pet \(type\) has by default. ![$](../../.gitbook/assets/exclaim.gif) Small changes have a massive impact on the speed ![$](../../.gitbook/assets/exclaim.gif) |
|       Food: | list | The food this pet \(type\) eats. This setting must be a list of valid [config items](configitems.md) |
|       LeashItem: | string | The item this pet \(type\) can be leashed with. This setting must be a valid [config item](configitems.md) |
|       LeashFlags: | string | A comma separated list of valid [Leash Flags](../../systems/leashflag.md) |
|       CustomRespawnTimeFactor: | int | This setting allows to change the respawn times pet pet \(type\). The value will be added on top of the value from the main config. |
|       CustomRespawnTimeFixed: | int | This setting allows to change the respawn times pet pet \(type\). The value will be added on top of the value from the main config. |

