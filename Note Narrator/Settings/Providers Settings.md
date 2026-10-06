---
title: Providers Settings
description: Add and configure text to speech providers, including several of the same type, with their own API keys and parallel generation limits.
tags:
  - note-narrator
  - settings
  - providers
  - elevenlabs
publish: true
permalink: note-narrator/settings/providers
plugin-version: 1.1.0
updated: 2026-10-05
---

# Providers Settings

A **provider** is a named connection to a text to speech service: its **type**, its **credentials**, and how many chunks may generate at once. Narrator profiles choose which provider they use. See [[Profiles Settings]].

![[settings-providers-list.png]]

## The provider list

- **+** adds a provider, and also adds a narrator profile for it named **Default (provider name)**, so a new provider is usable straight away. On mobile it is an "Add provider" row below the list.
- Select a provider to open its page.
- Drag the handle to reorder.
- To remove a provider, open it and press **Delete provider** at the bottom of its page. You can also select a row in the list and press the Delete key.
- A provider with **no API key** shows a warning marker.

> [!info] Several providers of the same type
> You can add more than one provider of the same type. For example, two ElevenLabs providers for a personal and a work account, each with its own API key and its own rate limits. Narrator profiles then pick whichever account they should use.

> [!warning] Deleting a provider deletes its profiles
> If narrator profiles use the provider, you are asked to confirm, and those profiles are deleted with it. That includes the automatic **Default (provider name)** profile.

## A provider's page

![[settings-provider-page.png]]

### Connection

| Setting | What it does |
| --- | --- |
| **Name** | How the provider is listed here and when a profile picks a provider |
| **Type** | Which service it connects to. Only ElevenLabs is available today |
| **API key** | Chosen from Obsidian's secret storage, not saved in the plugin's settings file |

> [!info] Where the key lives
> The key is stored with Obsidian's [secret storage](https://docs.obsidian.md/plugins/guides/secret-storage). Only the **name** of the secret is saved (`elevenlabs-api-key` by default), so the key never appears in your vault or synced settings, and other plugins can share the same secret.

### Generation

Rate limits belong to an account, not a voice, so parallel generation is set **per provider**.

| Setting | Default | Greyed out when | What it does |
| --- | --- | --- | --- |
| **Generate chunks in parallel** | Enabled | never | Generate more than one chunk ahead of playback at once |
| **Max parallel chunk generation** | 2 | Parallel is off | Chunks generating at once (minimum 2). Recommended 2 to 5. Has a reset button |
| **Max parallel background chunk generation** | 1 | never | The same limit for notes generating in the background, whether you used **Move to background** or **Generate in background**. Kept low so it does not compete with a read you are listening to. Recommended 1 to 3 |

> [!warning] Rate limits
> If the service answers with a rate limit (HTTP 429), Note Narrator retries with backoff and falls back to one chunk at a time for the rest of that read. See [[Long Notes and Chunking]].

## ElevenLabs models

The model is part of a narrator profile, not the provider. See [[Profiles Settings]].

| Model | Character limit per request |
| --- | --- |
| Eleven v3 (research preview) | 5,000 |
| Eleven Multilingual v2 | 10,000 |
| Eleven Flash v2.5 | 40,000 |

See [[Setting Up ElevenLabs]] for creating a key.
