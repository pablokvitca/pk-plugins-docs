---
title: Profiles Settings
description: Narrator profiles bundle a provider, its voice settings and optional reading overrides, and appear in the panel's narrator dropdown.
tags:
  - note-narrator
  - settings
  - profiles
publish: true
permalink: note-narrator/settings/profiles
plugin-version: 1.1.1
updated: 2026-10-06
---

# Profiles Settings

A **narrator profile** is a named way of reading. It has:

- a **name**
- a **provider** (see [[Providers Settings]])
- that provider type's **voice settings**
- a **Show in panel dropdown** toggle
- optional **reading overrides** of the [[General Settings|General]] defaults

![[settings-profiles-list.png]]

## Default narrator

The **Default narrator** dropdown at the top of the tab picks the profile used for reads. The panel's Narrator dropdown changes the same setting. Inside a profile, **Use as default narrator** does the same.

## The profile list

- **+** adds a profile using your first provider. Change its provider on its page. Adding a provider on the Providers tab also adds a profile called **Default (provider name)**.
- Select a profile to open its page. The current default shows a "Default" marker, and a profile whose provider has no API key shows a warning marker.
- Drag to reorder.
- To remove a profile, open it and press **Delete narrator profile** at the bottom of its page (or select a row and press the Delete key). You cannot delete your last profile, so the button is greyed out then.

## A profile's page

![[settings-profile-page.png]]

### Name and provider

The settings at the top of the page, without a heading:

| Setting | What it does |
| --- | --- |
| **Name** | How the profile appears in the panel and here |
| **Provider** | Which provider generates the audio. Switching to a provider of another type resets the voice settings |
| **Show in panel dropdown** | Offer the profile in the panel's Narrator dropdown. The active profile is always shown, even if this is off |
| **Use as default narrator** | Makes this the active profile |
| **Delete narrator profile** | At the bottom of the page. Removes the profile |

### Voice (ElevenLabs)

| Setting | Default | What it does |
| --- | --- | --- |
| **Voice** | Rachel | Voices from the provider's account (first 100), with a refresh button |
| **Model** | Eleven Multilingual v2 | Eleven v3 (research preview), Multilingual v2 or Flash v2.5 |
| **Stability** | 0.5 | Lower is more expressive and varied, higher is steadier. On v3 it maps to Creative, Natural and Robust presets |
| **Similarity boost** | 0.75 | How closely the output matches the original voice |

> [!caution] Eleven v3 is a research preview
> It can mispronounce or invent words more than Multilingual v2, and Professional Voice Clones are not fully optimized for it yet.

### Reading overrides

Each row is a dropdown that starts on **Use default (...)**, showing the current General value. Pick a value to override it for this profile only.

| Override | Choices | Greyed out when |
| --- | --- | --- |
| Read note title | Use default, On, Off | never |
| Skip title when it repeats the first heading | Use default, On, Off | Read note title is off (effective value) |
| Read note properties | Use default, On, Off | never |
| Skip Markdown comments | Use default, On, Off | never |
| Don't read comment delimiter symbols | Use default, On, Off | Comments are skipped (effective value) |
| Announce comments as "Comment: ..." | Use default, On, Off | Comments are skipped (effective value) |
| Text chunker | Use default, Markdown-aware, Sentence-only | never |
| Max heading depth for sections | Use default, 1 to 6 | Chunker is not Markdown-aware (effective value) |
| Override skip sections by heading | Toggle. Off uses the General patterns | Chunker is not Markdown-aware |
| Skip sections by heading | This profile's own list, one regex per line | Not overriding, or chunker not Markdown-aware |

> [!example] Two profiles for different content
> - **Journal**: a warm voice, Read note properties off, reads everything.
> - **Docs**: a steady voice, Skip sections by heading set to `Changelog`, Max heading depth 3.
>
> Switch between them in the panel's Narrator dropdown.

## How profiles affect saved audio

Saved audio records a **fingerprint** of the profile's voice settings (provider type, voice, model, stability, similarity boost). Renaming a profile, moving it to another account, or changing reading overrides does not change it, but changing the voice, model or voice sliders does. If the selected profile's fingerprint differs from a note's saved audio, the Read button becomes **Regenerate with new narrator**. See [[Saving Audio]].

> [!info] Coming later
> Choosing a profile automatically by note folder is on the [[Roadmap]].
