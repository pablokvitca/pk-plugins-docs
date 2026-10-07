---
title: The Panel
description: A tour of the Note Narrator sidebar panel, including the idle layout, buttons, progress display and menu.
tags:
  - note-narrator
  - usage
  - panel
publish: true
permalink: note-narrator/using/the-panel
plugin-version: 1.1.2
updated: 2026-10-06
---

# The Panel

The panel lives in the right sidebar. Open it from the ribbon icon, the note toolbar icon, or the **Read note aloud** command. Opening it never starts generation on its own.

![[panel-idle.png]]

## Layout, top to bottom

1. **Selected note.** A "Read: Note title" line for the note you are viewing. The panel follows the active note as you switch between notes. If a read is already in progress for a different note, a "Currently reading: Other note" line appears under it, so switching notes never hides what is playing.
2. **Narrator.** Dropdown of your narrator profiles that have **Show in panel dropdown** on (plus the active one). Picking one makes it the active narrator. See [[Profiles Settings]].
3. **Note stats.** Total characters, total chunks, and approximate average characters and words per chunk, computed as soon as a note is open, before you click anything.
4. **Saved audio status.** Only when the note has linked audio. Shows a green "up to date" line, or an amber warning when the note changed ("outdated") or the audio was made with a different narrator, with a small delete button for the saved file. See [[Saving Audio]].
5. **Action buttons.** See below.
6. **Status, time and progress.** Elapsed, total and remaining time, "Part X of Y, Z% complete", and the generation bar.
7. **Playback controls.** See [[Playback Controls]].
8. **Speed and volume.** Live sliders, each can be hidden in settings. See [[Appearance Settings]].
9. **Background jobs.** Notes queued, generating or finished in the background. Click one to play it. See [[Background Generation]].

> [!note] Disabled, not hidden
> Buttons that do not apply right now (for example Previous part on a single-chunk read, or Play saved when there is no saved audio) are shown disabled rather than removed, so the layout does not jump around.

## Action buttons

| Button | What it does |
| --- | --- |
| **Play saved** | Plays the note's existing saved audio with no regeneration. |
| **Read** | Generates and plays the note. Relabels itself to **Regenerate** when the note changed since the audio was made, and to **Regenerate with new narrator** when the selected profile's voice settings differ from the saved audio's. While busy it reads "Reading". |
| **Cancel** | Stops an in-progress generation. |
| **Background** | Generates the note in the background without playing it. When the saved audio is up to date it regenerates it instead (its tooltip says **Regenerate in background**). Reads **Move to background** while the note is reading (stops playback, keeps generating), and **Ready in background** once its background job has finished. Disabled when there is nothing to do. See [[Background Generation#What the button says]]. |

The **Compact buttons** setting turns these into icon-only buttons with tooltips. Narrow panels do this automatically.

![[panel-buttons-states.png]]

## The generation bar

A segmented bar with one segment per chunk:

- **Ready** chunks are filled.
- Chunks **generating right now** pulse.
- The chunk **currently playing** is outlined.
- Chunks not started yet are empty.

![[panel-generation-bar.png]]

## Time readout

Choose what the times mean with the **Time display** setting: full totals across the whole read (unfinished parts shown as "+N parts"), just the current part, or both. See [[Appearance Settings]].

## The title-bar menu

The **⋮** menu in the panel's title bar has **Clear Note Narrator files**, which deletes a note's linked audio file and removes the properties. It also clears the note's finished background job from the list, if it has one. You are asked to confirm first. You can hide it with the **Show "clear Note Narrator files"** setting. See [[Files Settings]].

## The note toolbar icon

Each note has an audio-lines icon in its top-right toolbar (next to the **⋯** menu). It opens the panel.

It changes to a waveform with a check badge when the note's saved audio is up to date with both the note and the selected narrator profile, so you can tell at a glance.

![[toolbar-icon-states.png]]
