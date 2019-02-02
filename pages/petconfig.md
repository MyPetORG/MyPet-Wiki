# Pet Configuration

The _pet-config.yml_ file contains all MyPet-Type specific settings. All other settings can be found in the main config \([config.yml](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/pages/configfile/README.md)\).

| Setting | Type | Default | ![$](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/wiki/images/premium.gif) | Description |
| :--- | :---: | :---: | :---: | ---: |
| **MyPet:** |  |  |  |  |
|   **Pets:** |  |  |  |  |
| These settings are per MyPet-Type |  |  |  |  |
|     **&lt;MyPet-Type-Name&gt;:** |  |  |  |  |
|       HP: | double | `20` | - | The maximum HP the pet \(type\) has by default. |
|       Speed: | double | `0.3` | - | The running speed the pet \(type\) has by default. ![$](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/wiki/images/exclaim.gif) Small changes have a massive impact on the speed ![$](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/wiki/images/exclaim.gif) |
|       Food: | list |  | - | The food this pet \(type\) eats. This setting must be a list of valid [config items](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/pages/configitems/README.md) |
|       LeashItem: | string |  | - | The item this pet \(type\) can be leashed with. This setting must be a valid [config item](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/pages/configitems/README.md) |
|       LeashFlags: | string |  | - | A comma separated list of valid [Leash Flags](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/pages/leashflag/README.md) |
|       CustomRespawnTimeFactor: | int | `0` | - | This setting allows to change the respawn times pet pet \(type\). The value will be added on top of the value from the main config. |
|       CustomRespawnTimeFixed: | int | `0` | - | This setting allows to change the respawn times pet pet \(type\). The value will be added on top of the value from the main config. |

