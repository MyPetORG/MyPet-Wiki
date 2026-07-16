---
description: >-
  The MyPet Configurator is a web-based editor that connects to your live server
  and edits its configuration.
icon: browser
---

# Configurator

The **MyPet Configurator** is a web-based editor for your server's MyPet configuration. It connects to your running server, loads its real configuration, and writes your changes back when you are ready.

Everything the Configurator edits can also be edited by hand — it reads and writes the same files in your `plugins/MyPet` directory, in the same formats. The Configurator gives you a visual UI, validation as you type, and previews of how things will actually look in-game.

{% content-ref url="opening-a-session.md" %}
[opening-a-session.md](opening-a-session.md)
{% endcontent-ref %}

{% content-ref url="saving-changes.md" %}
[saving-changes.md](saving-changes.md)
{% endcontent-ref %}

## What it edits

| Editor              | File                    | Documentation                                                                     |
| ------------------- | ----------------------- | --------------------------------------------------------------------------------- |
| **Main Config**     | `config.yml`            | [config.yml](../getting-started/configuration/config.yml.md)                      |
| **Pet Config**      | `pet-config.yml`        | [pet-config.yml](../getting-started/configuration/pet-config.yml/)                |
| **Pet Shops**       | `pet-shops.yml`         | [pet-shops.yml](../getting-started/configuration/pet-shops.yml.md)                |
| **Mob XP Rewards**  | `exp-config.yml`        | [exp-config.yml](../getting-started/configuration/exp-config.yml.md)              |
| **Skilltrees**      | `skilltrees/*.st.json`  | [Creating Custom Skilltrees](../skilltree-creation/creating-custom-skilltrees/)   |
| **Locale**          | `locale/*.properties`   | [Translation](../getting-started/systems/translation.md)                           |
| **Menus**           | `gui/menus/*.json`      | —                                                                                  |

## Layout

### Topbar

The topbar shows the Configurator version on the left, and on the right a button to toggle light/dark mode, a language selector, and a link to this documentation.

### Sidebar

The sidebar lists every editor, grouped into categories: General, Pets, Experience, Skilltrees, Locale, and Menus. Select one to open it.

At the top of the sidebar is the session status — `Live`, `Connecting…`, `Awaiting trust`, or `Offline` — along with how long the session has left and the MyPet and Minecraft versions of the connected server. At the bottom is the `Review & Save` button, described in [Saving Changes](saving-changes.md).

### Editor

The selected editor fills the rest of the window. Larger editors divide their settings into tabs — the Main Config, for example, has `Database`, `Respawn`, `Hunger`, `Experience`, `Permissions`, `Names`, `Skills`, and `Updates`.

The [Skilltrees](../skilltree-creation/creating-custom-skilltrees/) editor works differently to the rest: instead of a form, it draws every skilltree as a node on one canvas.

## Trying it without a server

Open [https://editor.mypet-plugin.de/#demo](https://editor.mypet-plugin.de/#demo), or click `Try the demo` on the Configurator's start screen. This loads example data locally so you can explore every editor. Nothing is saved, and no server is involved.
