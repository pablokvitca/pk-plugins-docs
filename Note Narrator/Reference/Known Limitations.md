---
title: Known Limitations
description: Current limitations and caveats of Note Narrator.
tags:
  - note-narrator
  - reference
  - limitations
publish: true
permalink: note-narrator/reference/known-limitations
plugin-version: 1.1.1
updated: 2026-10-06
---

# Known Limitations

Things that do not work the way you might expect yet. Many have a planned fix on the [[Roadmap]].

## Content

> [!bug] HTML comments are read aloud
> `<!-- HTML comments -->` are not stripped and are read as literal text, symbols included. Obsidian comments (`%% ... %%`) work and have their own settings.

- Sentence and word level highlighting are not available.
- Images are silently skipped. They are not described.
- A `%%` comment containing heading-like text (`# ...`) can throw off section boundaries.

## Saved audio

- **Staleness is whole-note.** The hash covers the full note, so editing anything, even outside what was read (for example after reading a selection), marks the audio outdated.
- **Replace keeps the old filename.** With "Replace existing file", a narrator change keeps the original filename (with the old voice name in brackets) and only replaces the contents.
- **Multi-part files are concatenated bytes.** Chunks are joined without re-muxing the MP3 stream. This works with ElevenLabs output but is not strictly spec-correct MP3 concatenation.
- **Part navigation can fall back.** During Play saved, if chunk-affecting settings changed since the audio was made, or the byte lengths do not add up, the file plays as a single non-navigable piece even though the note still says "up to date". Regenerate to fix it.
- **Clear has no undo** for the properties. The file goes to trash per your vault setting.

## Background generation

- **Out-of-date jobs are not flagged.** If you edit a note (or change its narrator) after its background job started, the job's card does not say so, and clicking it plays the old text. Pressing **Read** or the **Background** button replaces it with a fresh job. **Move to background** on a read of an edited note moves the old read as it is.

## Playback and highlighting

- No scrubbing to an arbitrary time, only relative rewind and skip.
- Chunk and section highlight positions are proportional estimates and can be a word or two off at a boundary.
- Highlighting needs Editing view. It cannot draw in Reading view.
- Neither highlighting nor scroll-to-current applies to selection reads.

## ElevenLabs

- Only the first **100 voices** on a provider's account are listed in a profile's voice dropdown.
- The rate limit fallback to one chunk at a time only lasts for the read in progress. Parallel generation is set per provider.
- Eleven v3 is a research preview and can mispronounce or invent words. Professional Voice Clones are not fully optimized for it yet.
- **Auto-generate on open** spends credits on every open of a missing or outdated note.

## Platform

- Requires Obsidian 1.13.1 or newer.
- Requires an ElevenLabs account. ElevenLabs is the only provider type so far, though you can add several ElevenLabs providers. No offline or local voice yet.

> [!question] Found something not listed?
> Open an issue on the [GitHub repository](https://github.com/pablokvitca/note-narrator).
