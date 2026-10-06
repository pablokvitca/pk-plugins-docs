---
title: Settings Overview
description: Every Note Narrator setting, grouped by the six tabs of the settings screen, with defaults.
tags:
  - note-narrator
  - settings
publish: true
permalink: note-narrator/settings/overview
plugin-version: 1.1.0
updated: 2026-10-05
---

# Settings Overview

Open **Settings, Note Narrator**. A tab bar at the top switches between six sections, each with its own page here.

![[settings-tab-overview.png]]

| Tab | Page | About |
| --- | --- | --- |
| **General** | [[General Settings]] | Default reading settings and default playback speed |
| **Providers** | [[Providers Settings]] | Connections to TTS services: API keys and parallel generation |
| **Profiles** | [[Profiles Settings]] | Narrator profiles: provider, voice settings, dropdown toggle, reading overrides |
| **Appearance** | [[Appearance Settings]] | Panel display, rewind and skip, and highlighting |
| **Performance** | [[Performance Settings]] | How playback starts |
| **Files** | [[Files Settings]] | Saving audio, linking it in notes, and cleanup |

> [!info] Greyed out, not hidden
> A setting that does not apply right now, because another setting is off, is **greyed out** instead of disappearing. Turn the setting it depends on back on and it becomes usable again.

> [!tip] Upgrading from an older version
> Your old voice, model, API key and parallel-generation settings are migrated automatically into one provider and one narrator profile named **Default**. See [[Providers Settings]] and [[Profiles Settings]].

## Defaults at a glance

| Setting | Default |
| --- | --- |
| **Providers** | One ElevenLabs provider, key secret name `elevenlabs-api-key` |
| Generate in parallel / Max parallel / Max background parallel (per provider) | On / 2 / 1 |
| **Profiles** | One profile, "Default" |
| Profile voice / model | Rachel (`21m00Tcm4TlvDq8ikWAM`) / Eleven Multilingual v2 |
| Stability / Similarity boost | 0.5 / 0.75 |
| Show in panel dropdown | Enabled |
| Reading overrides | None (inherit General) |
| Read selection instead of whole note | Enabled |
| Read note title / properties | Enabled / Disabled |
| Skip title when it repeats the first heading | Enabled |
| Skip Markdown comments | Enabled |
| Text chunker / Max heading depth | Markdown-aware / 2 |
| Default playback speed | 1x |
| Compact buttons | Disabled |
| Show volume / speed slider | Enabled / Enabled |
| Time display | Current part |
| Background job display | Minimal card |
| Rewind / Skip forward | 15s / 15s |
| Highlight while reading | Disabled |
| Highlight granularity / style | Chunk / Margin marker |
| Scroll-to-current button | Enabled |
| Keep generating when starting another note | Enabled |
| Start playback immediately / Quick start | Enabled / Enabled |
| Quick start size | 150 words (750 characters) |
| Save generated audio to a file | Disabled |
| Link saved audio in the note | **Enabled** (turning on saving also turns this on) |
| Save location | Same folder as the note |
| Custom folder path | `Note Narrator Audio` |
| On regenerate | Replace existing file |
| Auto-generate on open | Disabled |
| Show clear files button | Enabled |
| Auto-clean missing files | Enabled |

> [!note] Settings are per vault
> Settings live in the vault's plugin `data.json`. API keys do not: they are in Obsidian's secret storage. See [[Setting Up ElevenLabs]].
