# Pet Configuration

The *pet-config.yml* file contains all MyPet-Type specific settings.
All other settings can be found in the main config ([config.yml](configfile)).

|  Setting  |  Type  |  Default  |  Since / (P)  |  Description  |
| --------  |        |           |               |               |
|**MyPet:**|||||
|&nbsp;&nbsp;**Pets:**|||||
|  These settings are per MyPet-Type  |||||
|&nbsp;&nbsp;&nbsp;&nbsp;**&lt;MyPet-Typ-Name&gt;:**|||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;HP:|  double  |  `20`  |  -  |The maximum HP the pet (type) has by default.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Speed:|  double  |  `0.3`  |  -  |The running speed the pet (type) has by default. :!: Small changes have a massive impact on the speed :!:|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Food:|  list  |    |  -  |The food this pet (type) eats. This setting must be a list of valid [config items](configitem)|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;LeashItem:|  string  |    |  -  |The item this pet (type) can be leashed with. This setting must be a valid [config item](configitem)|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;LeashFlags:|  string  |    |  -  |A comma separated list of valid [Leash Flags](leashflag)|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;CustomRespawnTimeFactor:|  int  |  `0`  |  -  |This setting allows to change the respawn times pet pet (type). The value will be added on top of the value from the main config.|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;CustomRespawnTimeFixed:|  int  |  `0`  |  -  |This setting allows to change the respawn times pet pet (type). The value will be added on top of the value from the main config.|