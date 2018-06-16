# Pet Shop Configuration

The *pet-shops.yml* file contains the shops where players can buy pets.
Pet shops are exclusively available in the ![$](/wiki/images/premium.gif) premium version of MyPet.

----

You can create as many shops as you want, but all of them need different IDs (`<shop-id>`)

----


| Setting | Type | Default | Description |
| :------- | :------: |  :------: |  :------: | -------: |
|**Shops:**||||
|&nbsp;&nbsp;**&lt;shop-id&gt;:**|    |    |`<shop-id>` can be chosen freely but needs to be unique for every shop|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Name:|  string  |  ` `  |The name that will be shown in the shop overview|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Balance**:||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Type:|  string  |  `Private`  |TODO|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Pets**:||||
|  These settings are per pet that's been sold  ||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**&lt;unique-string&gt;:**||||
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Name:|  string  |    |The name the pet will have|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Description:|  list of strings  |    |The description that will be shown when hovering the shop item|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Position:|  integer  |  `0`  |The slot in the inventory the pet item will have in the shop|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Exp:|  double  |  `0`  |The XP the pet will have|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Price:|  double  |  `100`  |The price the player has to pay in order to get the pet|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Skilltree:|  string  |    |The skilltree the pet will have|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PetType:|  string  |    |The mob type of the pet|
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Options:|  list of strings  |    |These work exaclty like the parameters for the pet create admin command. You can see an example in the comment of the first default shop|