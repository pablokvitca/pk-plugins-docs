---
title: Saving Audio
description: Save generated audio as mp3 files, link them from your notes, detect when they are outdated, and regenerate or clear them.
tags:
  - note-narrator
  - usage
  - saved-audio
publish: true
permalink: note-narrator/using/saving-audio
plugin-version: 1.1.0
updated: 2026-10-05
---

# Saving Audio

Saving turns each read into an `.mp3` in your vault so you can replay it later without spending more credits.

> [!abstract] Three layers
> 1. **Save generated audio to a file**: write the `.mp3`. Disabled by default.
> 2. **Link saved audio in the note**: record the link and tracking data in the note's frontmatter. **Enabled by default**, and turning on layer 1 turns it on too.
> 3. **Auto-generate on open**: keep audio fresh in the background. Disabled by default. Needs layers 1 and 2.

Settings are in [[Files Settings]]. Settings that do not apply, such as the property names while saving is off, are greyed out.

## Saving

With saving on, the file is written as soon as **generation** finishes, not when playback ends. Files go in the note's own folder or a folder you choose (created if missing). Filenames include the voice, for example `My Note (Rachel).mp3`.

## Linking and staleness

With linking on, the note gets frontmatter properties recording the audio link, a content hash, the file path, a timestamp, a fingerprint of the narrator profile's voice settings, and each chunk's duration. Full list in [[Frontmatter Properties]].

The hash lets the panel tell you whether the audio still matches the note:

> [!success] Saved audio is up to date
> The note has not changed since the audio was generated. **Play saved** is ready.

> [!warning] Saved audio is outdated
> The note has changed. **Read** becomes **Regenerate**. Play saved still plays the old audio.

> [!note] Everything counts
> The hash covers the note's full content, even if you only read a selection, so any edit marks the audio outdated. Note Narrator's own properties are always excluded. Add other properties (for example a last-modified timestamp another plugin updates) to **Extra properties to exclude from staleness hashing**.

![[panel-saved-status.png]]

## Playing saved audio

**Play saved** plays the file immediately with no generation. Previous/Next part, highlighting and scroll-to-current also work because the saved chunk durations let the file be sliced back into parts.

> [!caution] Only while up to date
> Part navigation and highlighting during Play saved need the note to be up to date, and the chunk count to still match. If reading or chunking settings changed since the audio was made (chunker style, heading depth, skip patterns, quick start, model), the file plays as one piece. Regenerate to fix it.

## Regenerating

**On regenerate** decides what happens to the old file:

- **Replace existing file** (default): overwrite in place. If the voice changed, the file keeps its original name with the old voice in brackets, only its contents change.
- **Keep old versions**: make a new file each time.

## Auto-generate on open

Opening a note silently regenerates and saves its audio if it is missing or outdated. It does not play and does not disturb anything already playing.

> [!danger] Costs credits
> Every open of a missing or outdated note makes ElevenLabs requests. Be careful with notes you edit often.

## Clearing

**Clear Note Narrator files** (panel **⋮** menu, or the delete button on the status line) removes a note's audio file and its properties after a confirmation. The file goes to the trash according to your vault's deletion preference. The properties cannot be restored. If the note has a finished background job, it is cleared from the list too. One still generating is kept, and its new audio is saved when it finishes.

If a linked file is deleted or moved outside Note Narrator, the plugin can quietly remove the stale properties so the note does not show a misleading "outdated" status. That is **Auto-clean up properties when saved file is missing** (enabled by default).

## Where does it go?

> [!info] On the roadmap
> Moving the tracking data off the note and onto the audio file, saving outside the vault, and saving to cloud storage are all planned. See [[Roadmap]].
