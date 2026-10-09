---
title: Roadmap
description: What Note Narrator has shipped recently, what is in progress, and what is planned or under consideration.
tags:
  - note-narrator
  - roadmap
publish: true
permalink: note-narrator/roadmap
plugin-version: 1.1.5
updated: 2026-10-09
---

# Roadmap

> [!warning] Not a promise
> This is direction, not a schedule. Ideas move between milestones, get reshaped, or get dropped. Version numbers show intended order, not dates.

## Recently shipped

- **1.1.5: fixes and disclosure.** Background notes edited since they were generated, or made with another narrator, are marked **Outdated** on their card. A new **Protect audio shared with copied notes** setting (on by default) controls the check that keeps a copied note from overwriting or trashing the original's audio; it's the only time Note Narrator looks at other notes, and it's now described in [[Privacy and Network Use]]. Every dropdown marks its default option, ElevenLabs error messages are kept short, and a development-only dependency was updated for a security advisory.
- **1.1.4: fixes.** Edit a note while it's being read, or play its outdated saved audio, and **Read** now offers **Regenerate** instead of staying a disabled "Reading". It also comes back as **Read** if you delete the saved audio while it plays. Only an `.mp3` counts as a note's saved audio, so an edited audio path property can no longer get another file overwritten or trashed, and a copy of a note no longer replaces or trashes the audio it shares with the original. Background notes whose audio is saved are freed from memory and play from the vault, and unsaved finished notes are capped by the new **Unsaved finished notes kept in memory** setting (see [[Performance Settings]]). Notes saved with Windows (CRLF) line endings no longer have their properties read aloud or their highlight drift, a property edited just before Read is spoken with its new value, and audio saved by **Auto-generate on open** with quick start on keeps its parts for Previous/Next instead of playing as one piece.
- **1.1.3: fixes.** Deleting a note while its audio file is being written no longer leaves that file behind or shows a "Failed to save audio file" notice. If you disable the plugin or select **Read** at that moment instead, the finished audio is still saved and linked. Also more automated tests for the panel, the plugin's commands, and folders being moved or deleted.
- **1.1.2: fixes.** Selecting **Read** or **Background** for a note that **Auto-generate on open** is still generating now takes over from it instead of generating the note a second time, and deleting the note stops it without leaving an audio file behind. After you switch narrator profile, the panel's status line says when a note's saved audio was made with a different narrator, and the toolbar icon only shows its check badge for audio that matches the selected narrator. The Files setting now quotes the **Clear Note Narrator files** menu item as it appears.
- **1.1.1: fixes.** The background button is now labelled just **Background** (hover for whether it generates or regenerates). The note title is read together with the start of the note instead of as a tiny first part followed by a pause. Read and **Background** work after you close the note's tab. Cancelling a read (or disabling the plugin) no longer saves its audio, deleting a note while it is being read no longer leaves an audio file or a background card behind, and **Auto-generate on open** no longer generates a note that is already being read or generated, and stops when you disable the plugin. Unit tests now run on every build.
- **1.1.0: generate in background.** Generate a note's audio in the background without starting a read first, from the panel's **Generate in background** button or the new **Generate note audio in background** command. The button follows the note: **Move to background** while it is reading, **Regenerate in background** when its saved audio is up to date, and **Ready in background** once its job has finished. Finished jobs can be cleared from the list, and deleting a note or its saved audio removes its job. Also fixed: pausing while the current part is still generating now stays paused, and audio for a note edited while it was generating no longer shows as up to date. See [[Background Generation]]. Also in 1.1.0: when the note title exactly matches its first heading, the title is no longer read twice (see **Skip title when it repeats the first heading** on [[General Settings]]).
- **Note Narrator is in Obsidian's community plugin directory.** Install it from **Settings → Community plugins → Browse** instead of BRAT. See [[Installation]].
- **1.0.0.** No user-facing changes over 0.17.1. It hardens the release process: the built `main.js` and `styles.css` now carry a GitHub build-provenance attestation, so anyone can verify they came from this repository's own source; a CSS rule was adjusted to drop a browser-support warning; and a type-resolution dependency (`moment`) is now declared directly instead of arriving indirectly through Obsidian's own package.
- **0.17.1:** keep generating the current note in the background when you start reading another one (on by default, see [[Background Generation]]); repaint the editor highlight immediately when a highlight setting changes; the note's toolbar icon and the panel's Regenerate label update correctly when switching notes; the custom save folder can no longer be pointed outside the vault; invalid or iOS-unsupported "Skip sections by heading" patterns are flagged as you type
- **0.17.0: providers and narrator profiles.** The settings screen is reorganised into six tabs (General, Providers, Profiles, Appearance, Performance, Files). Providers hold API keys and parallel-generation limits, and you can add several, even of the same type. Narrator profiles bundle a provider, voice settings, a dropdown toggle and optional reading overrides, and replace the old voice list and panel voices shortlist. Settings that do not apply are greyed out instead of hidden, and saving audio now turns on linking by default
- **0.17.0:** the note's toolbar icon switches to a waveform with a check badge when it has up-to-date saved audio, so you no longer need to open the panel to check
- Background generation with a job list, click to play, and a separate concurrency limit
- Volume slider and mute, plus optional speed and volume rows
- Full-audio time display modes with "+N parts" for ungenerated chunks
- Highlight while reading (chunk and section granularity, three styles) and a scroll to current section button
- Skip sections by heading regex, and separate Markdown comment toggles
- Saved audio: up to date tracking, per-chunk parts for Previous/Next during Play saved, auto-generate on open
- Mobile support: tested on iPhone, iPad, iPad mini and visionOS, with touch-sized controls
- Configurable rewind and skip amounts and compact buttons

## What's still ahead

1.0.0 was a version number, not a feature-complete milestone. A few of the original "toward 1.0" goals are still open:

| Item | Why |
| --- | --- |
| **ElevenLabs credit usage and cost estimates** | Show remaining credits and an estimate before you read a long note |
| **Other TTS providers** | Providers already have a type and per-type settings, so this means implementing more types than ElevenLabs. Google Gemini is next. See [[Supported Platforms]] |
| **Local or offline voices** | Apple OS (Local) first: the text to speech built into macOS, iOS, iPadOS and visionOS. No key, no network, lower expressiveness. A local model may follow |
| **Auto-caption images** | Use a vision model to give images a short spoken description instead of skipping them |

## After 1.0

### 1.1

| Item | Notes |
| --- | --- |
| **HTML comment skipping fix** | `<!-- -->` comments are currently read aloud. A previous attempt did not hold up |
| **"Do not read aloud" delimiters** | A start and end marker, for example `---(start do not read aloud)---`, to exclude any region regardless of chunker |
| **Hide Note Narrator properties** | A toggle to hide its frontmatter from the rendered Properties view (feasibility is being investigated) |
| **Read out backlinks** | An option to speak the notes that link to this one. Disabled by default |
| **Better per-chunk saving** | Proper MP3 re-muxing, or saving chunks separately with a manifest |

### 2.0

| Item | Notes |
| --- | --- |
| **Save audio outside the vault** | For example a folder synced by iCloud, Google Drive or OneDrive, so audio does not bloat vault sync |
| **Cloud storage** | Save to and stream from remote storage such as S3 |

## Under consideration

Not scheduled yet.

- **Default narrator profile by note folder.** Notes under `Journal/` use one profile, notes under `Work/` another, without touching the panel dropdown each time.
- **Move tracking data onto the audio file.** Today six properties live on every note. Storing the metadata with the audio file would keep notes clean.
- **More content filters.** Toggles to skip code blocks, inline code, blockquotes, tags, tables, image embeds, emojis and other syntax.
- **Per-section and chapter bookmarks.**
- **Sentence and word level highlighting.** Needs word timing from the provider to stay in sync.

> [!question] Have an idea?
> Open an issue on the [GitHub repository](https://github.com/pablokvitca/note-narrator). See also [[Known Limitations]] for the gaps these items address.
