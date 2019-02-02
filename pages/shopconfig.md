# Pet Shop Configuration

The _pet-shops.yml_ file contains the shops where players can buy pets. Pet shops are exclusively available in the ![$](https://github.com/xXKeyleXx/MyPet-Wiki/tree/07680434e1278c970819d5e9518888598106688b/wiki/images/premium.gif) premium version of MyPet.

You can create as many shops as you want, but all of them need different IDs \(`<shop-id>`\)

| Setting | Type | Default | Description |
| :--- | :---: | :---: | :---: |
| **Shops:** |  |  |  |
|   **&lt;shop-id&gt;:** |  |  | `<shop-id>` can be chosen freely but needs to be unique for every shop |
|         Name: | string |  | The name that will be shown in the shop overview |
|       **Balance**: |  |  |  |
|         Type: | string | `Private` | TODO |
|       **Pets**: |  |  |  |
| These settings are per pet that's been sold |  |  |  |
|         **&lt;unique-string&gt;:** |  |  |  |
|           Name: | string |  | The name the pet will have |
|           Description: | list of strings |  | The description that will be shown when hovering the shop item |
|           Position: | integer | `0` | The slot in the inventory the pet item will have in the shop |
|           Exp: | double | `0` | The XP the pet will have |
|           Price: | double | `100` | The price the player has to pay in order to get the pet |
|           Skilltree: | string |  | The skilltree the pet will have |
|           PetType: | string |  | The mob type of the pet |
|           Options: | list of strings |  | These work exaclty like the parameters for the pet create admin command. You can see an example in the comment of the first default shop |

