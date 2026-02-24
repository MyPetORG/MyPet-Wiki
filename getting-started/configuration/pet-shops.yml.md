---
icon: shop
---

# pet-shops.yml

The `pet-shops.yml` file contains the shops where players can buy pets.

You can create as many shops as you want, but all of them need different IDs (`<shop-id>`). Each shop can be opened by its id with the `/petshop <shop-id>` command. Every item in the shop needs a unique ID too (`<id>`).

{% hint style="info" %}
`<shop-id>` can be chosen freely but must be unique for every shop.\
This corresponds to `<shop-name>` in the shop permission node.
{% endhint %}

## Settings

Below is the structure and types for entries in `pet-shops.yml`.

* Shops:
  * `<shop-id>`:
    * Name (string): The name that will be shown in the shop overview
    * Balance (string): Wallet type. Not yet documented. Default is `Private`.
    * Pets:
      * `<id>`:
        * Name (string): The name the pet will have
        * Description (list of strings): The description that will be shown when hovering the shop item
        * Position (integer): The slot in the inventory the pet item will have in the shop
        * Exp (double): The XP the pet will have
        * Price (double): The price the player has to pay in order to get the pet
        * Skilltree (string): The skilltree the pet will have
        * PetType (string): The mob type of the pet
        * Options (list of strings): These work exactly like the parameters for the `pet create` admin command

## Example template

```yaml
# pet-shops.yml

shops:
  <shop-id>:
    Name: "<Shop Display Name>"
    Balance: "<wallet>"
    Pets:
      <id>:
        Name: "<Pet Name>"
        Description:
          - "First line of description"
          - "Second line"
        Position: 10
        Exp: 0.0
        Price: 100.0
        Skilltree: "<skilltree-id>"
        PetType: "<mob-type>"
        Options:
          - "option1:value"
          - "option2:value"
```

## Notes

* Each shop must have a unique `<shop-id>`.
* Each pet item inside a shop must have a unique `<id>`.
* Open a shop with: `/petshop <shop-id>`.
