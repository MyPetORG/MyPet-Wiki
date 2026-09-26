---
description: >-
  Every option accepted by /petadmin create and by the Options: list of a
  pet-shops.yml entry, per pet.
---

# Pet Creation Options

Creation options set what a Pet looks like and starts out as. The same strings
are used in two places:

* `/petadmin create <player> <type> [options...]` — for example
  `/petadmin create Notch panda main-gene:lazy baby`
* the `Options:` list of a `pet-shops.yml` entry — one option per list item

Options that take a value use `key:value` with no space. Flags are written on
their own. Unknown values are rejected with the list of valid ones; in game,
tab-completion offers every option and value for the pet you typed.

{% hint style="info" %}
Options that change the mob itself are skipped for
[MythicMobs custom creatures](custom-pet-models.md) — MythicMobs spawns the
entity, not MyPet. `skilltree:` and `name:` still apply.
{% endhint %}

### Every pet

| Option | Values |
| ------ | ------ |
| `skilltree:<name>` | any skilltree the pet is eligible for |
| `name:<text>` | the pet's name |

### Per pet

Pets not listed here take only the options above.

| Pet | Option | Values | Notes |
| --- | ------ | ------ | ----- |
| Armadillo | `baby` |  |  |
| Axolotl | `baby` |  |  |
|  | `variant:` | `lucy`, `wild`, `gold`, `cyan`, `blue` |  |
| Bee | `angry` |  |  |
|  | `baby` |  |  |
|  | `has-nectar` |  |  |
| Blaze | `fire` |  |  |
| Camel | `baby` |  |  |
|  | `saddle` |  |  |
|  | `tamed` |  |  |
| CamelHusk | `baby` |  |  |
|  | `saddle` |  |  |
| Cat | `baby` |  |  |
|  | `collar:` | `white`, `orange`, `magenta`, `light_blue`, `yellow`, `lime`, `pink`, `gray`, `light_gray`, `cyan`, `purple`, `blue`, `brown`, `green`, `red`, `black` |  |
|  | `tamed` |  |  |
|  | `variant:` | `all_black`, `black`, `british_shorthair`, `calico`, `jellie`, `persian`, `ragdoll`, `red`, `siamese`, `tabby`, `white` (plus anything a datapack adds) |  |
| Chicken | `baby` |  |  |
|  | `variant:` | `cold`, `temperate`, `warm` (plus anything a datapack adds) |  |
| CopperGolem | `oxidation:` | `unaffected`, `exposed`, `weathered`, `oxidized` |  |
|  | `waxed` |  |  |
| Cow | `baby` |  |  |
|  | `variant:` | `cold`, `temperate`, `warm` (plus anything a datapack adds) |  |
| Creeper | `powered` |  |  |
| Dolphin | `baby` |  |  |
| Donkey | `baby` |  |  |
|  | `chest` |  |  |
|  | `saddle` |  |  |
|  | `tamed` |  |  |
| Drowned | `baby` |  |  |
| Enderman | `block:` | any block material | Any block material, e.g. `stone` or `minecraft:grass_block`. |
|  | `screaming` |  |  |
| Fox | `baby` |  |  |
|  | `variant:` | `red`, `snow` |  |
| Frog | `variant:` | `cold`, `temperate`, `warm` (plus anything a datapack adds) |  |
| GlowSquid | `baby` |  |  |
| Goat | `baby` |  |  |
|  | `noLeftHorn` |  |  |
|  | `noRightHorn` |  |  |
|  | `screaming` |  |  |
| HappyGhast | `baby` |  |  |
|  | `harness:` | `white`, `orange`, `magenta`, `light_blue`, `yellow`, `lime`, `pink`, `gray`, `light_gray`, `cyan`, `purple`, `blue`, `brown`, `green`, `red`, `black` |  |
| Hoglin | `baby` |  |  |
| Horse | `baby` |  |  |
|  | `color:` | `white`, `creamy`, `chestnut`, `brown`, `black`, `gray`, `dark_brown` |  |
|  | `saddle` |  |  |
|  | `style:` | `none`, `white`, `whitefield`, `white_dots`, `black_dots` |  |
|  | `tamed` |  |  |
| Husk | `baby` |  |  |
| Llama | `baby` |  |  |
|  | `chest` |  |  |
|  | `tamed` |  |  |
|  | `variant:` | `creamy`, `white`, `brown`, `gray` |  |
| MagmaCube | `size:` | whole number `1`–`8` |  |
| Mooshroom | `baby` |  |  |
|  | `variant:` | `red`, `brown` |  |
| Mule | `baby` |  |  |
|  | `chest` |  |  |
|  | `saddle` |  |  |
|  | `tamed` |  |  |
| Nautilus | `saddle` |  |  |
| Ocelot | `baby` |  |  |
| Panda | `baby` |  |  |
|  | `hidden-gene:` | `normal`, `lazy`, `worried`, `playful`, `brown`, `weak`, `aggressive` | Not visible on its own; it is passed on when breeding. |
|  | `main-gene:` | `normal`, `lazy`, `worried`, `playful`, `brown`, `weak`, `aggressive` | `brown` and `weak` are recessive in vanilla: the panda only *looks* brown/weak when **both** genes are set to it. |
| Parrot | `tamed` |  |  |
|  | `variant:` | `red`, `blue`, `green`, `cyan`, `gray` |  |
| Phantom | `size:` | whole number `1`–`64` |  |
| Pig | `baby` |  |  |
|  | `saddle` |  |  |
|  | `variant:` | `cold`, `temperate`, `warm` (plus anything a datapack adds) |  |
| Piglin | `baby` |  |  |
| PolarBear | `baby` |  |  |
| Pufferfish | `puff:` | `none`, `semi`, `fully` |  |
| Rabbit | `baby` |  |  |
|  | `variant:` | `brown`, `white`, `black`, `black_and_white`, `gold`, `salt_and_pepper`, `the_killer_bunny` |  |
| Salmon | `variant:` | `small`, `medium`, `large` |  |
| Sheep | `baby` |  |  |
|  | `color:` | `white`, `orange`, `magenta`, `light_blue`, `yellow`, `lime`, `pink`, `gray`, `light_gray`, `cyan`, `purple`, `blue`, `brown`, `green`, `red`, `black` |  |
|  | `sheared` |  |  |
| SkeletonHorse | `baby` |  |  |
|  | `saddle` |  |  |
|  | `tamed` |  |  |
| Slime | `size:` | whole number `1`–`8` |  |
| Sniffer | `baby` |  |  |
| SnowGolem | `derp` |  |  |
| Squid | `baby` |  |  |
| Strider | `baby` |  |  |
|  | `saddle` |  |  |
| TraderLlama | `baby` |  |  |
|  | `chest` |  |  |
|  | `tamed` |  |  |
|  | `variant:` | `creamy`, `white`, `brown`, `gray` |  |
| TropicalFish | `body-color:` | `white`, `orange`, `magenta`, `light_blue`, `yellow`, `lime`, `pink`, `gray`, `light_gray`, `cyan`, `purple`, `blue`, `brown`, `green`, `red`, `black` |  |
|  | `pattern-color:` | `white`, `orange`, `magenta`, `light_blue`, `yellow`, `lime`, `pink`, `gray`, `light_gray`, `cyan`, `purple`, `blue`, `brown`, `green`, `red`, `black` |  |
|  | `pattern:` | `kob`, `sunstreak`, `snooper`, `dasher`, `brinely`, `spotty`, `flopper`, `stripey`, `glitter`, `blockfish`, `betty`, `clayfish` |  |
| Turtle | `baby` |  |  |
| Vex | `glowing` |  |  |
| Villager | `baby` |  |  |
|  | `profession:` | `armorer`, `butcher`, `cartographer`, `cleric`, `farmer`, `fisherman`, `fletcher`, `leatherworker`, `librarian`, `mason`, `nitwit`, `none`, `shepherd`, `toolsmith`, `weaponsmith` (plus anything a datapack adds) |  |
|  | `variant:` | `desert`, `jungle`, `plains`, `savanna`, `snow`, `swamp`, `taiga` (plus anything a datapack adds) |  |
| Wolf | `angry` |  |  |
|  | `baby` |  |  |
|  | `collar:` | `white`, `orange`, `magenta`, `light_blue`, `yellow`, `lime`, `pink`, `gray`, `light_gray`, `cyan`, `purple`, `blue`, `brown`, `green`, `red`, `black` |  |
|  | `tamed` |  |  |
|  | `variant:` | `ashen`, `black`, `chestnut`, `pale`, `rusty`, `snowy`, `spotted`, `striped`, `woods` (plus anything a datapack adds) |  |
| Zoglin | `baby` |  |  |
| Zombie | `baby` |  |  |
| ZombieHorse | `baby` |  |  |
|  | `saddle` |  |  |
|  | `tamed` |  |  |
| ZombieNautilus | `saddle` |  |  |
| ZombieVillager | `baby` |  |  |
|  | `profession:` | `armorer`, `butcher`, `cartographer`, `cleric`, `farmer`, `fisherman`, `fletcher`, `leatherworker`, `librarian`, `mason`, `nitwit`, `none`, `shepherd`, `toolsmith`, `weaponsmith` (plus anything a datapack adds) |  |
|  | `variant:` | `desert`, `jungle`, `plains`, `savanna`, `snow`, `swamp`, `taiga` (plus anything a datapack adds) |  |
| ZombifiedPiglin | `baby` |  |  |

Values listed for Minecraft `1.21.11`.

{% hint style="warning" %}
This page is generated from the plugin source by
`.github/scripts/creation_options.py` in the MyPet repo. Edit the generator (or
the pet's `CREATION_SPECS` field), not this page.
{% endhint %}
