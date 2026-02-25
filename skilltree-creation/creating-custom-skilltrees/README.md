---
description: MyPet's web-based Skilltree Creator makes creating custom Skilltrees easy.
icon: layer-plus
---

# Creating Custom Skilltrees

Skilltrees were designed to be customized to fit the needs of the server running MyPet. Because of this, we have designed an easy-to-use [_Skilltree Creator_](https://skilltree.mypet-plugin.de/) which provides a visual UI for editing .st.json files used by the MyPet plugin, with live validation, autosave, and convenient import/export.&#x20;

The Skilltree Creator can be accessed by navigating your browser to [https://skilltree.mypet-plugin.de/](https://skilltree.mypet-plugin.de/) or on a desktop with Java installed by double-clicking the `MyPet.jar`. You can also build a local version from the [source code](https://github.com/MyPetORG/MyPet-SkilltreeCreator). Most parts of the Skilltree Creator should be self-explanatory.

## Skilltree Creator Parts

### Topbar

<figure><img src="../../.gitbook/assets/Skilltree Toolbar.webp" alt=""><figcaption></figcaption></figure>

The Skilltree Topbar, from left to right, shows the current version of the tool, includes buttons for importing, loading default skilltrees, and exporting a ZIP file of your work, a button to manually save progress, autosave status, a button to toggle light/dark mode for the creator, a language selector, and a button link to the skilltree documentation.

#### Import

{% hint style="warning" %}
This function will overwrite all existing work in the Skilltree Creator!
{% endhint %}

The `Import` button opens a dialog where existing skilltree files can be uploaded from the local computer, either singularly in the .st.json format or a ZIP file of multiple compressed .st.json skilltree files. The Creator will validate all files before loading them and will fail with an error if the files are not formatted correctly. Using a validator like [jsonlint](https://jsonlint.com/) can be helpful to identify and correct any errors in existing files.

Once successfully uploaded, the imported skilltrees will appear in the [Skilltree List](./#skilltree-list).

#### Load Defaults

{% hint style="warning" %}
This function will overwrite all existing work in the Skilltree Creator!
{% endhint %}

The `Load Defaults` button will load the default Combat, Utility, PvP, Ride, and Farm skilltree configurations, which can then be edited as desired.

#### Export Zip

The `Export Zip` button will zip the current progress in the Skilltree Creator Tool and open a download dialog where you can save the ZIP file to the local computer. This can serve to save your progress and create a backup that can be uploaded again to the Skilltree Creator later via the [Import](./#import) function or can also be unzipped and the individual skilltree files can be uploaded into your `plugins/MyPet/skilltrees` directory in your Minecraft server.

#### Save & Autosave Status

These show the current save status of the current Skilltree Creator session. The Creator automatically saves your work when making changes, so the `Save` button will usually be unavailable. While it is still recommended to regularly backup your work using the [Export Zip](./#export-zip) function, this allows for quick recovery even if the browser tab or window are closed (as long as session data isn't cleared from your browser on close).

### Skilltree List

<figure><img src="../../.gitbook/assets/Skilltree List.webp" alt="Image of the Skilltree List in the MyPet Skiltree Creator populated with the default Combat, Utility, PvP, Ride, and Farm skilltrees" width="336"><figcaption></figcaption></figure>

In the skilltree list/overview you can create and delete skilltrees and drag to reorder them. Select a skilltree from this list to edit its properties, appearance in the Skilltree GUI, eligible pets, requirements, notifications, and skills.

The Skilltree List can also be collapsed and expanded again using the button at the top of the Skilltree List to allow for more room in your browser window when navigating the Skilltree Editor.

### Skilltree Editor

The Skilltree Editor will open when a skilltree is selected from the Skilltree List. This allows you to edit the selected skilltree as desired using the tabs:

* [Properties](properties.md): ID, inheritance, weight
* [Appearance](appearance.md): Name, Icon material (with preview), Description with live MC‑style preview
* [Eligible Pets](eligible-pets.md): Choose which mobs are eligible; you can also include all current and future mobs
* [Requirements](requirements.md): Min/Max level and additional requirement lines (Skilltree/Permission/custom)
* [Notifications](notifications.md): Chat templates keyed by level specifications, with live preview
* [Skills](skills/): Add/remove skills from the registry and edit their upgrade payloads and levels
