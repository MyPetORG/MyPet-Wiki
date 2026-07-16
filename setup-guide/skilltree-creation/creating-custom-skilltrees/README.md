---
description: MyPet's web-based Configurator makes creating custom Skilltrees easy.
icon: layer-plus
---

# Creating Custom Skilltrees

Skilltrees were designed to be customized to fit the needs of the server running MyPet. Because of this, the [MyPet Configurator](../../configurator/) includes a visual skilltree editor, which reads and writes the `.st.json` files used by the plugin.

To get started, run `/mypet editor` in-game and open the link it gives you, then select `Skilltrees` in the sidebar. See [Opening a Session](../../configurator/opening-a-session.md) for the full walkthrough, or [try the demo](https://editor.mypet-plugin.de/#demo) to explore with example data and no server.

## Skilltree Canvas

Every skilltree on your server is a node on one canvas, with edges drawn between trees that require one another. Select a node to open the [Inspector](./#inspector) for that tree.

The toolbar above the canvas provides:

* `+ New skilltree` — create a new skilltree.
* `Search skilltrees…` — filter as you type. Press `Enter` to fit the view to the matches, `Escape` to clear.
* `Undo` / `Redo` — step back and forth through your changes.
* `Species…` — journey mode. Pick a species to spotlight only the trees a pet of that species can travel through.
* `More actions` — per-tree actions such as `Duplicate` and `Delete skilltree`.

{% hint style="warning" %}
Deleting a skilltree that other trees require leaves those trees showing a dangling-reference badge. The Configurator warns you before deleting.
{% endhint %}

## Inspector

The Inspector docks beside the canvas when you select a skilltree, and is where you edit it. Instead of tabs it uses collapsible sections, so you can keep more than one open at a time — handy when you want to adjust a requirement while watching the skills timeline.

* [Properties](properties.md): ID, inheritance, weight
* [Appearance](appearance.md): Name, Icon material (with preview), Description with live MC‑style preview
* [Eligible Pets](eligible-pets.md): Choose which mobs are eligible; you can also include all current and future mobs
* [Requirements](requirements.md): Min/Max level and additional requirement lines (Skilltree/Permission/custom)
* [Notifications](notifications.md): Chat templates keyed by level specifications, with live preview
* [Skills](skills/): Add/remove skills from the registry and edit their upgrade payloads and levels
* `Timeline`: an overview of when each skill upgrade fires as a pet levels up

`Properties`, `Appearance`, and `Skills` are open by default; the rest start collapsed.

The `{ }` button shows the raw `.st.json` for the selected tree, which you can copy or download.

## Saving

Your changes are held in the browser until you apply them with `Review & Save`. See [Saving Changes](../../configurator/saving-changes.md).

## Skilltree Files

Skilltrees are stored as `.st.json` files in the `plugins/MyPet/skilltrees` directory of your server. You can still edit these by hand — the Configurator reads and writes the same format. Files it cannot parse are shown on the canvas as errors and saved back unchanged, so a typo in one file will not cost you the rest of your work.

{% hint style="info" %}
Upgrading from MyPet 3? The plugin migrates your existing skilltrees on startup: legacy `&` colour codes become MiniMessage, and renamed mob types (`PigZombie`, `Snowman`) are updated. See [What are Skilltrees?](../what-are-skilltrees.md) for the file format.
{% endhint %}
