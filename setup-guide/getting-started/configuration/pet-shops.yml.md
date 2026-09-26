---
description: Contains options for pet shops.
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
    * Position (integer): The order of the shop's icon in the `/petshop` selection menu, lowest first. Shops without a `Position` are listed after the positioned ones, in file order.
    * Icon (section): The item shown for the shop in the selection menu.
      * Material (string): The item type, e.g. `CHEST`. Default is `chest`.
      * Glowing (boolean): Whether the item has the enchantment glint. Default is `false`.
    * Balance (string): Wallet type. Default is `Private`.
    * Pets:
      * `<id>`:
        * Name (string): The name the pet will have
        * Description (list of strings): The description that will be shown when hovering the shop item
        * Position (integer): The slot in the inventory the pet item will have in the shop
        * Exp (double): The XP the pet will have
        * Price (double): The price the player has to pay in order to get the pet
        * Skilltree (string): The skilltree the pet will have
        * PetType (string): The mob type of the pet — a vanilla type name (`IronGolem`) or the section name of a [custom creature](../systems/custom-pet-models.md) from `pet-config.yml` (`Capybara`). An entry whose `PetType` is missing or not registered is left out of the shop, and the server log says which entry was skipped and why.
        * Options (list of strings): These work exactly like the parameters for the `pet create` admin command — [Pet Creation Options](../systems/pet-creation-options.md) lists every option and value, per pet. Options that change the mob itself (`baby`, `variant:`, `saddle`, …) are skipped for [source-driven custom creatures](../systems/custom-pet-models.md) such as MythicMobs pets — see the note below.

## Example template

```yaml
# pet-shops.yml

shops:
  <shop-id>:
    Name: "<Shop Display Name>"
    Position: 0
    Icon:
      Material: "CHEST"
      Glowing: false
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
* Open a shop **for someone else** with: `/petshop <shop-id> <player>` — the form to use
  from the console, a command block, or a menu plugin button (`petshop <shop-id> %player%`).
  It requires `mypet.command.shop.other` for player senders, and does not require the
  target to hold `mypet.shop.access.<shop-id>`.
* `Options:` entries that change the mob (`baby`, `variant:`, `saddle`, `tamed`, …) do nothing when `PetType` is a [MythicMobs custom creature](../systems/custom-pet-models.md), because MythicMobs spawns the entity rather than MyPet. `Skilltree:` and `Name:` still apply. The server log names any option that was skipped at checkout.
