---
title: Screenshot Checklist
description: Every screenshot placeholder in the docs, what it should show, and whether it has been captured.
tags:
  - meta
  - docs
publish: false
updated: 2026-09-27
---

# Screenshot Checklist

Each placeholder in the docs is a `> [!todo] Screenshot needed: ...` callout. To fill one in:

1. Capture the image and save it in the plugin's `Screenshots/` folder (for Note Narrator: `Note Narrator/Screenshots/`) with the exact filename below (PNG, ideally 2x, cropped to the relevant UI, light and dark theme both if practical).
2. In the page, replace the whole `[!todo]` callout with `![[filename.png]]` and, if useful, a caption line.
3. Tick it off here.

> [!tip] Finding leftovers
> Search the vault for `Screenshot needed` to list every placeholder still open.

## Getting started

- [x] `hero-panel-and-note.png` on [[Note Narrator]]. Note in Editing view, panel open mid-playback, margin marker visible
- [x] `install-brat-add-plugin.png` on [[Installation]]. BRAT's Add a beta plugin dialog
- [x] `settings-add-provider-menu.png` on [[Quick Start]], [[Providers Settings]] and each provider's setup guide. The Providers list with the **+** menu open (the menu is drawn with Obsidian's menu markup: a script can't open a real one in the settings window)
- [x] `settings-provider-elevenlabs.png`, `-openai`, `-google-gemini`, `-amazon-polly` on each setup guide (OpenAI's also on [[Quick Start]] and [[Providers Settings]], Amazon Polly's also on [[Providers Settings]]). The provider's page, key set, with the guide link
- [x] `settings-profile-voice-elevenlabs.png`, `-openai`, `-google-gemini`, `-amazon-polly` on each setup guide and [[Profiles Settings]] (OpenAI's also on [[Quick Start]]). The profile page down to the Voice section
- [x] `open-panel-ribbon-and-toolbar.png` on [[Quick Start]]. Ribbon icon and toolbar icon called out
- [x] `panel-reading.png` on [[Quick Start]]. Panel while reading

## Using

- [x] `panel-idle.png` on [[The Panel]]. Idle panel with a note open
- [x] `panel-buttons-states.png` on [[The Panel]]. Read, Regenerate, Regenerate with new narrator, compact
- [x] `panel-generation-bar.png` on [[The Panel]]. Ready, generating, current and empty segments
- [x] `toolbar-icon-states.png` on [[The Panel]]. Normal and 0.17 saved states
- [x] `playback-controls-row.png` on [[Playback Controls]]. Labeled transport row and sliders
- [x] `slider-compact-popover.png` on [[Playback Controls]]. Narrow panel pill with popover
- [x] `panel-saved-status.png` on [[Saving Audio]]. Up to date and outdated status lines
- [x] `highlight-margin-marker.png`, `highlight-background.png` and `highlight-underline.png` on [[Highlighting and Scrolling]]. One per style
- [x] `background-jobs-list.png` on [[Background Generation]]. One generating, one finished

## Settings

- [x] `settings-tab-overview.png` on [[Settings Overview]]. The tab bar, General selected
- [x] `settings-general.png` on [[General Settings]] (plus a variant with comment skipping off)
- [x] `settings-profiles-list.png` on [[Profiles Settings]]. Default narrator dropdown and two profiles
- [x] `settings-profile-page.png` on [[Profiles Settings]]. Profile, Voice and Reading overrides groups
- [x] `settings-appearance.png` on [[Appearance Settings]]. Highlighting on so dependents are enabled
- [x] `settings-performance.png` on [[Performance Settings]]
- [x] `settings-files.png` on [[Files Settings]]. Saving on, plus a variant with saving off (greyed out)
