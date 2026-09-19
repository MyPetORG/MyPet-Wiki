---
description: >-
  This page describes the automatic plugin updater functionality and what you
  need to know to use it.
icon: wrench
---

# Auto Updater

### Enable the Auto Updater <a href="#enable-the-auto-updater" id="enable-the-auto-updater"></a>

By default the plugin checks for plugin updates but doesn't download them. You can enable the download by activating it in the [config.yml](../configuration/config.yml.md) by setting `MyPet.Update.Download` to `true`.

The downloaded jar is placed in the server's `update` folder and loaded automatically on the next server start, replacing the running jar in place and renaming it to match the new version (e.g. `MyPet-4.0.0.jar`).

The `In-Background` option controls timing: when `true`, the download runs on a background thread so it doesn't hold up server startup; when `false`, the plugin waits for the download to finish before continuing to boot.
