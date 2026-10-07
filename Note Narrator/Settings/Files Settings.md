---
title: Files Settings
description: Settings for saving audio files, linking them in note frontmatter, staleness tracking, regeneration and cleanup.
tags:
  - note-narrator
  - settings
  - saved-audio
publish: true
permalink: note-narrator/settings/files
plugin-version: 1.1.2
updated: 2026-10-06
---

# Files Settings

The **Files** tab controls saved audio. Concepts are explained in [[Saving Audio]]. It has three groups: **Saving audio**, **Linking in the note**, and **Cleanup**.

![[settings-files.png]]

![[settings-files-saving-off.png]]

With saving off, the options that depend on it are greyed out.

> [!important] Turning on saving turns on linking
> Linking is **enabled by default**, and switching **Save generated audio to a file** on also switches **Link saved audio in the note** on, even if you had turned it off. Saved audio is most useful when the note tracks it.

Everything except the first setting is **greyed out until saving is on**, and the property settings, regeneration, auto-generate and cleanup are also greyed out while linking is off.

## Saving audio

| Setting | Default | Greyed out when | What it does |
| --- | --- | --- | --- |
| **Save generated audio to a file** | Disabled | never | Saves each read as an `.mp3` in the vault |
| **Save location** | Same folder as the note | Saving is off | Same folder, or a custom folder |
| **Custom folder path** | `Note Narrator Audio` | Saving is off, or location is not Custom folder | Vault-relative folder, created if missing. Empty falls back to the default |
| **On regenerate** | Replace existing file | Saving or linking is off | **Replace existing file** or **Keep old versions** |
| **Auto-generate on open** | Disabled | Saving or linking is off | Silently regenerates missing or outdated audio when a note opens |

## Linking in the note

| Setting | Default | Greyed out when | What it does |
| --- | --- | --- | --- |
| **Link saved audio in the note** | Enabled | Saving is off | Writes the link and tracking data to frontmatter and enables up to date / outdated tracking |
| **Link property** | `note_narrator_audio` | Saving or linking is off | Property holding the link to the audio |
| **Hash property** | `note_narrator_audio_hash` | Saving or linking is off | Content hash used to detect staleness |
| **Path property** | `note_narrator_audio_path` | Saving or linking is off | Raw vault path, used internally to find the file |
| **Timestamp property** | `note_narrator_audio_timestamp` | Saving or linking is off | When the audio was generated |
| **Narrator property** | `note_narrator_audio_voice` | Saving or linking is off | A fingerprint of the narrator profile's voice settings. Detects a narrator change |
| **Chunk durations property** | `note_narrator_audio_chunk_durations` | Saving or linking is off | Each chunk's `[duration, byte length]`, used to slice the file into parts |
| **Extra properties to exclude from staleness hashing** | empty | Saving or linking is off | One property key per line. Ignored when checking whether the note changed |

> [!tip] Change the property names if you like
> Every property name is editable to match an existing vault convention. An empty entry falls back to the default. Existing notes keep their old property names until regenerated, so change these before you build up saved audio.

## Cleanup

| Setting | Default | Greyed out when | What it does |
| --- | --- | --- | --- |
| **Show "Clear Note Narrator files" menu item and delete button** | Enabled | Saving or linking is off | Enables the panel menu item and the status-line delete button |
| **Auto-clean up properties when saved file is missing** | Enabled | Saving or linking is off | Removes stale properties if the linked file no longer exists |

> [!danger] Auto-generate on open spends credits
> It makes provider requests every time you open a note that is missing audio or outdated. Leave it off for notes you edit constantly.

> [!warning] Deleting is permanent for properties
> Clearing moves the file to trash per your vault setting, but the properties are removed with no undo.
