---
description: >-
  This page describes the automatic plugin updater functionality and what you
  need to know to use it.
icon: wrench
---

# Auto Updater

### Enable the Auto Updater <a href="#enable-the-auto-updater" id="enable-the-auto-updater"></a>

By default the plugin checks for plugin updates but doesn't download them. You can enable the download by activating it in the [config.yml](../configuration/config.yml.md) by setting `MyPet.Update.Download` to `true`.

From there, you have two additional options, including `ReplaceOld`, which will load the update on the next server start, or `In-Background`, which will immediately download the updated plugin jar.
