---
description: >-
  Frequently asked questions about MyPet 4, collected from the MyPet Discord.
icon: circle-question
---

# FAQ

## Pets & NBT

**Can I manually set the NBT of a pet — for example a baby zombie, or a "baby" version of a mob via the scale attribute?**\
MyPet saves an NBT **snapshot** of the mob at the moment it becomes (or updates) a pet — on capture, on storage, on player quit, and so on. Whatever is on the mob at that point stays on the pet. So spawn the mob with the NBT you want, then leash it:

```
/summon minecraft:zombie ~ ~ ~ {IsBaby:1b}
/summon minecraft:cow ~ ~ ~ {attributes:[{id:"minecraft:scale",base:0.4}]}
```

## Custom pet models

**How do I add the Capybara (or the Chameleon)?**\
MyPet bundles the **model**, not a finished pet type — there is no `Capybara` until you define it once. With **BetterModel** or **ModelEngine** installed, the quickest way is the built-in editor:

1. Run `/mypet editor` in-game and open the link.
2. Go to **pet-config**, click **Create custom pet**, and pick your provider.
3. Leave the **MyPet default** model tab selected and choose **capybara**.
4. Name it `Capybara`, pick a host mob (`Pig` is a good default), then **Create**.
5. Click **`Review & Save`**, then **`Apply Changes`**.

`Apply Changes` reloads the server for you — it writes the file, registers the pet type, and installs the bundled model, so there is nothing else to run. Then give one out with `/petadmin create <player> mypet:capybara`.

Prefer editing the file yourself? Add this under `MyPet.Pets` in `pet-config.yml` and run `/mypet reload config`:

```yaml
MyPet:
  Pets:
    Capybara:
      Host: Pig
      HP: 20.0
      Speed: 0.3
      LeashItem: lead
      Model:
        Provider: BetterModel   # or ModelEngine
        Id: capybara            # bundled — MyPet installs the .bbmodel for you
```

Either way, name it exactly `Capybara` (or `Chameleon`) — the bundled skilltrees match on that name. Full walkthrough, including the Chameleon: [Bundled Models — Capybara & Chameleon](getting-started/systems/bundled-pet-models.md).

**Why does `/petadmin create <player> mypet:capybara` say the pet type is invalid?**\
Because no custom creature named `Capybara` is defined yet, or its section is missing the `Host:` key. A `MyPet.Pets.<Name>` section only becomes a new pet type when it has `Host:` — without it the section is read as settings for an existing type. See [Bundled Models — Capybara & Chameleon](getting-started/systems/bundled-pet-models.md).

**My model's animations have custom names — I could remap sit and the others, but where do I set the walk animation?**\
You don't set it in MyPet. MyPet only plays the **event** animations — `spawn`, `despawn`, `sit`, `sit_loop`, `unsit`, `attack` — and those names can be remapped per pet type (see [pet-config.yml → Model animations](getting-started/configuration/pet-config.yml/#model-animations)). Movement animations like walking and idling are handled by the rendering plugin itself (ModelEngine / BetterModel / ItemsAdder), not by MyPet — so either rename your walk animation to the name that plugin expects (usually `walk`), or check whether the plugin lets you target a different animation name. See [Custom Pet Models](getting-started/systems/custom-pet-models.md#animations).

## Updating

**Can I update my server from MyPet 3.x (e.g. 3.14.2) straight to 4.0, or will there be incompatibilities and data loss?**\
Yes, you can update directly. MyPet 4 was designed for automatic conversion — replace the plugin jar, start the server, and all of your plugin data (pets, levels, names, inventories) is migrated on its own. Take a backup first anyway: the migration is one-way, with no downgrade path back to 3.x. Full details in [Updating from MyPet 3 to 4](getting-started/updating-from-3-to-4.md).
