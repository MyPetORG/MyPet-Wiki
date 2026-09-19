---
description: Pet Shop Configuration
---

# pet-shops.yml

The _`pet-shops.yml`_ file contains the shops where players can buy pets.

You can create as many shops as you want, but all of them need different IDs (`<shop-id>`). Each shop can be opened by this it with the `/petshop <shop-id>` command. Every item in the shop needs a unique ID too (`<id>`).

| Setting                | Type            | Description                                                                                                                                                                      |
| ---------------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Shops:                 |                 |                                                                                                                                                                                  |
|   \<shop-id>:          |                 | <p><code>&#x3C;shop-id></code> can be chosen freely but needs to be unique for every shop</p><p><em>(This is <code>&#x3C;shop-name></code> in the shop permission node)</em></p> |
|         Name:          | string          | The name that will be shown in the shop overview                                                                                                                                 |
|       Balance:         |                 |                                                                                                                                                                                  |
|         Type:          | string          | TODO                                                                                                                                                                             |
|       Pets:            |                 |                                                                                                                                                                                  |
|         \<id>:         |                 |                                                                                                                                                                                  |
|           Name:        | string          | The name the pet will have                                                                                                                                                       |
|           Description: | list of strings | The description that will be shown when hovering the shop item                                                                                                                   |
|           Position:    | integer         | The slot in the inventory the pet item will have in the shop                                                                                                                     |
|           Exp:         | double          | The XP the pet will have                                                                                                                                                         |
|           Price:       | double          | The price the player has to pay in order to get the pet                                                                                                                          |
|           Skilltree:   | string          | The skilltree the pet will have                                                                                                                                                  |
|           PetType:     | string          | The mob type of the pet                                                                                                                                                          |
|           Options:     | list of strings | These work exaclty like the parameters for the pet create admin command.                                                                                                         |
