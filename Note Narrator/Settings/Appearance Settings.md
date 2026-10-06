---
title: Appearance Settings
description: Settings for how the panel looks and what its controls do, plus the follow-along highlighting settings.
tags:
  - note-narrator
  - settings
  - appearance
  - highlighting
publish: true
permalink: note-narrator/settings/appearance
plugin-version: 1.1.0
updated: 2026-10-05
---

# Appearance Settings

The **Appearance** tab has two groups: **Panel** and **Highlighting**.

![[settings-appearance.png]]

## Panel

| Setting | Default | What it does |
| --- | --- | --- |
| **Compact buttons** | Disabled | Play saved, Read, Cancel and the background button become icon-only with tooltips, at every panel size |
| **Show volume slider in panel** | Enabled | Shows the volume slider and mute button |
| **Show playback speed slider in panel** | Enabled | Shows the speed slider |
| **Time display** | Show current part times | **Show full times**, **Show current part times**, or **Show full times + current part times** (full totals with the current part in parentheses). Ungenerated parts show as "+N parts" |
| **Background job display** | Minimal card | **Minimal card**, **Compact row** or **Full callout**. See [[Background Generation]] |
| **Rewind seconds** | 15s | 5, 10, 15, 20, 25, 30, 45 or 60 |
| **Skip forward seconds** | 15s | Same options, set independently |

## Highlighting

| Setting | Default | Greyed out when | What it does |
| --- | --- | --- | --- |
| **Highlight while reading** | Disabled | never | Marks the playing text in the editor. Needs Editing view |
| **Highlight granularity** | Chunk | Highlighting is off | **Chunk** moves per audio request. **Section** moves least often (Markdown-aware chunker) |
| **Only highlight the section heading** | Disabled | Highlighting is off, or granularity is not Section | Highlights just the heading line |
| **Highlight style** | Margin marker | Highlighting is off | **Margin marker**, **Background wash**, or **Underline** |
| **Scroll-to-current button** | Enabled | never | Adds the **Scroll to current section** button to the playback controls. Works with highlighting off |

See [[Highlighting and Scrolling]] for how it looks and its limits, and [[Playback Controls]] for the controls the rewind and skip settings change.

> [!info] Sentence and word granularity
> Not offered yet. See [[Roadmap]].
