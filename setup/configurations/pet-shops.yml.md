---
description: Pet Shop Configuration
---

# pet-shops.yml

The _pet-shops.yml_ file contains the shops where players can buy pets.

You can create as many shops as you want, but all of them need different IDs \(`<shop-id>`\)

| Setting | Type | Description |
| :--- | :---: | :---: |
| **Shops:** |  |  |
|   **&lt;shop-id&gt;:** |  | `<shop-id>` can be chosen freely but needs to be unique for every shop |
|         Name: | string | The name that will be shown in the shop overview |
|       **Balance**: |  |  |
|         Type: | string | TODO |
|       **Pets**: |  |  |
| These settings are per pet that's been sold |  |  |
|         **&lt;unique-string&gt;:** |  |  |
|           Name: | string | The name the pet will have |
|           Description: | list of strings | The description that will be shown when hovering the shop item |
|           Position: | integer | The slot in the inventory the pet item will have in the shop |
|           Exp: | double | The XP the pet will have |
|           Price: | double | The price the player has to pay in order to get the pet |
|           Skilltree: | string | The skilltree the pet will have |
|           PetType: | string | The mob type of the pet |
|           Options: | list of strings | These work exaclty like the parameters for the pet create admin command. You can see an example in the comment of the first default shop |

