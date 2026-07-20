---
description: How to start a Configurator session and connect it to your server.
icon: plug
---

# Opening a Session

The Configurator works on your server's real configuration, so you start it from in-game rather than by visiting a URL directly.

{% stepper %}
{% step %}
### Run the command

Run `/mypet editor` in-game. This requires the `MyPet.admin.editor` permission.

The plugin uploads your current configuration and replies with a clickable link. The link contains a one-time key, so treat it as private and do not share it.
{% endstep %}

{% step %}
### Open the link

Click the link to open the Configurator in your browser. It loads your server's configuration and shows `Connecting to your server`.
{% endstep %}

{% step %}
### Authorize the browser

The first time a browser connects, the Configurator shows `Authorize this browser` and asks you to run `/mypet editor trust <code>` in-game with the code it displays.

Only the player who opened the session can authorize it. Once you do, the session indicator in the sidebar changes to `Live`.
{% endstep %}

{% step %}
### Edit and save

Make your changes, then use [Review & Save](saving-changes.md) to write them back to the server.
{% endstep %}

{% step %}
### Close the session

Run `/mypet editor close` when you are finished. Sessions also expire on their own.
{% endstep %}
{% endstepper %}

## Commands

| Command                     | Description                                       |
| --------------------------- | ------------------------------------------------- |
| `/mypet editor`             | Start a session and get a link to open it.        |
| `/mypet editor trust <code>` | Authorize the browser that is trying to connect. |
| `/mypet editor close`       | End the active session.                           |

All three require the `MyPet.admin.editor` permission.

## Session status

The sidebar shows the state of the connection:

| Status          | Meaning                                                                        |
| --------------- | ------------------------------------------------------------------------------ |
| `Live`          | Connected and authorized. Changes can be saved.                                |
| `Connecting…`   | Establishing the connection to your server.                                    |
| `Awaiting trust` | Waiting for you to run `/mypet editor trust <code>` in-game.                   |
| `Offline`       | Not connected. Changes cannot be saved until a session is live.                |

The sidebar also counts down how long the session has left, and warns you with `Session expiring soon` before it ends.

{% hint style="warning" %}
Each link works for one session only. If you see `This editor session has ended`, run `/mypet editor` again and open the **fresh** link — reopening the old one will not work.
{% endhint %}

## Settings

The relevant settings live in the `config.yml` under `MyPet.WebEditor`:

| Setting        | Default                           | Description                                                |
| -------------- | --------------------------------- | ---------------------------------------------------------- |
| `Enabled`      | `true`                            | Set to `false` to disable `/mypet editor` entirely.        |
| `EditorUrl`    | `https://editor.mypet-plugin.de`  | The Configurator to link to. Change this if you self-host. |
| `BytebinUrl`   | `https://bytebin.mypet-plugin.de` | Relay used to transfer your configuration to the browser.  |
| `BytesocksUrl` | `wss://bytesocks.mypet-plugin.de` | Relay used for the live connection back to the server.     |

If the editor is disabled, `/mypet editor` replies with `The MyPet web editor is disabled in the server config.`

## Skill list

The editor's skill list is provided by your server: every skill registered at the time you run `/mypet editor` — including skills added by other plugins — appears in the skilltree editor with its fields and labels. Removing a plugin that registered a skill makes existing skilltree entries for it show up as validation errors.

## Security

Your configuration travels between your server and your browser through two relay services, so that neither has to reach the other directly. Your server does not need to be publicly reachable, and you do not need to open a port.

* The key that unlocks your configuration is in the `#` part of the link. Browsers never send that part to the web server, so the relays only ever hold data they cannot read.
* Every message between your browser and your server is signed after the initial hello, and your server rejects anything that is not.
* Only the player who opened the session can authorize a browser, and the code must match the browser that is currently waiting.

{% hint style="warning" %}
Only run `/mypet editor trust` with a code you can see in your own browser. The code identifies **which** browser you are authorizing, so typing a code from anywhere else would authorize someone else's.
{% endhint %}
