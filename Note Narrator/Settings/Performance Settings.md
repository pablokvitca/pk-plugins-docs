---
title: Performance Settings
description: Settings for how quickly playback starts, how a still-generating read is handled when you start another one, and how many unsaved finished notes stay in memory, including quick start.
tags:
  - note-narrator
  - settings
  - performance
publish: true
permalink: note-narrator/settings/performance
plugin-version: 1.1.4
updated: 2026-10-08
---

# Performance Settings

The **Performance** tab controls how quickly playback starts.

> [!info] Parallel generation moved
> How many chunks generate at once is now set **per provider**, because rate limits belong to the account. See [[Providers Settings#Generation|the provider's Generation group]].

![[settings-performance.png]]

| Setting | Default | Greyed out when | What it does |
| --- | --- | --- | --- |
| **Keep generating when starting another note** | Enabled | never | Starting a read (or Play saved) on a *different* note while one is still generating moves the current one to the background instead of discarding it, the same as pressing **Move to background**. Re-reading the same note is unaffected: that still restarts fresh. Selection reads are never moved. See [[Background Generation]] |
| **Unsaved finished notes kept in memory** | 5 | never | How many notes finished in the background, but not saved to the vault, are kept ready to play. Finishing one more clears the oldest, with a notice. **0** keeps them all. Notes with saved audio don't count: their audio plays from the vault. Clearing an empty field resets it to the default. See [[Background Generation]] |
| **Start playback immediately** | Enabled | never | Plays as soon as the first chunk is ready, instead of waiting for the whole note |
| **Quick start** | Enabled | Start immediately is off | Makes the first chunk artificially short (including the title and properties preamble) so playback starts sooner |
| **Quick start unit** | Words | Start immediately or Quick start is off | Size the first chunk in **Words** or **Characters** |
| **Quick start word count** | 150 | Unit is not Words, or the settings above are off | Target size in words. Recommended 50 to 300. Has a reset button |
| **Quick start character count** | 750 | Unit is not Characters, or the settings above are off | Slider 100 to 2000, step 50 |

> [!tip] Long notes
> Quick start matters most on long notes: the first sentence or two are generated alone, and the rest generates while you listen. See [[Long Notes and Chunking]].
