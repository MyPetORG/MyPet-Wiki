---
description: How the Configurator writes your changes back to the server.
icon: floppy-disk
---

# Saving Changes

The Configurator does not save as you type. Your changes are held in the browser until you apply them, so you can edit freely and review everything before anything reaches your server.

## Review & Save

`Review & Save` sits at the bottom of the sidebar. It is unavailable while there is nothing to save, and its tooltip reads `No unsaved changes`.

Clicking it lists every file you have changed, with a summary of what changed in each. If a file's only difference is formatting, it is listed as `Formatting only (no value changes)`.

Click `Apply Changes` to write the changes to your server. The plugin saves the files, reloads the affected configuration, and the Configurator reloads to show the result.

{% hint style="warning" %}
You need a [live session](opening-a-session.md) to save. If the sidebar shows anything other than `Live`, `Apply Changes` is unavailable and tells you why — for example `Connect a live session first — run /mypet editor and authorize the browser.`
{% endhint %}

## What gets written

Only the files you actually changed are written. Everything else is left alone, including:

* Files the Configurator does not edit.
* Skilltree files it could not parse. These appear as errors rather than being silently dropped, and are written back exactly as they were found, so a typo in one file cannot cost you the rest.

## Losing your changes

Your changes live in the browser tab until you apply them. They are **not** saved to your server, and they are **not** kept in your browser between visits.

{% hint style="warning" %}
Closing the tab loses unsaved work. If the session expires you will need a new one, and opening the fresh link reloads the editor — which also discards anything you had not applied. Use `Review & Save` as you go rather than saving everything at the end of a long editing run.
{% endhint %}
