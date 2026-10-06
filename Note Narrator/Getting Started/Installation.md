---
title: Installation
description: How to install Note Narrator with BRAT or manually, and what Obsidian version you need.
tags:
  - note-narrator
  - getting-started
publish: true
permalink: note-narrator/getting-started/installation
plugin-version: 1.0.0
updated: 2026-09-27
---

# Installation

## Requirements

| Requirement | Details |
| --- | --- |
| Obsidian | **1.13.1 or newer** (the settings tab uses the declarative settings API) |
| Platforms | Desktop and mobile. See [[Supported Platforms]] for what has been tested |
| Account | An [ElevenLabs](https://elevenlabs.io) account and API key |
| Network | Internet access to `api.elevenlabs.io` when you read or regenerate. See [[Privacy and Network Use]] |

## Option 1: Community plugins (recommended)

Note Narrator is in Obsidian's community plugin directory.

1. Open **Settings → Community plugins → Browse**.
2. Search for **Note Narrator** and select **Install**.
3. Enable it.

## Option 2: BRAT

[BRAT](https://github.com/TfTHacker/obsidian42-brat) installs plugins straight from GitHub and updates them for you. Use this if you want beta builds ahead of the community directory.

1. Install and enable **Obsidian42 - BRAT** from Community plugins.
2. Open the command palette and run **BRAT: Add a beta plugin for testing**.
3. Enter `pablokvitca/note-narrator`.
4. Enable **Note Narrator** under Settings, Community plugins.

> [!tip] Want betas?
> Stable releases are picked up automatically. To try in-development builds, enable "beta versions" for this plugin in BRAT's settings.

![[install-brat-add-plugin.png]]

## Option 3: Manual install

1. Download `main.js`, `manifest.json` and `styles.css` from the latest release on GitHub.
2. Copy them into `YourVault/.obsidian/plugins/note-narrator/`.
3. Restart Obsidian, then enable **Note Narrator** under Settings, Community plugins.

> [!note] Folder name matters
> The folder must be named `note-narrator`, matching the plugin id in `manifest.json`.

## Next step

Continue to the [[Quick Start]].
