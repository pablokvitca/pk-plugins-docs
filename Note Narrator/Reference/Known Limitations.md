---
title: Known Limitations
description: Current limitations and caveats of Note Narrator.
tags:
  - note-narrator
  - reference
  - limitations
publish: true
permalink: note-narrator/reference/known-limitations
plugin-version: 1.2.0
updated: 2026-10-26
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

- **Staleness is whole-note.** The hash covers the note's full text, so editing anything, even outside what was read (for example after reading a selection), marks the audio outdated. Properties only count with **Read note properties** on, except for audio saved before 1.1.6, which counts them until it's regenerated.
- **Replace keeps the old filename.** With "Replace existing file", a narrator change keeps the original filename (with the old voice name in brackets) and only replaces the contents.
- **Multi-part MP3 files are concatenated bytes.** MP3 chunks are joined without re-muxing the stream. This works with ElevenLabs', OpenAI's and Amazon Polly's output but is not strictly spec-correct MP3 concatenation. Google Gemini's WAV chunks are joined properly into one WAV file.
- **WAV files are large.** Google Gemini's audio is saved uncompressed (24 kHz, 16-bit mono), about three times the size of a typical MP3 of the same length.
- **Part navigation can fall back.** During Play saved, if chunk-affecting settings changed since the audio was made, or the byte lengths do not add up, the file plays as a single non-navigable piece even though the note still says "up to date". Regenerate to fix it.
- **Clear has no undo** for the properties. The file goes to trash per your vault setting.

## Background generation

- **Outdated jobs still play the old version.** A job whose note was edited (or whose narrator changed) after it was generated is marked **Outdated**, but playing it still plays the old text. Pressing **Read** or the **Background** button replaces it with a fresh job. **Move to background** on a read of an edited note moves the old read as it is.

## Playback and highlighting

- No scrubbing to an arbitrary time, only relative rewind and skip.
- Chunk and section highlight positions are proportional estimates and can be a word or two off at a boundary.
- Highlighting needs Editing view. It cannot draw in Reading view.
- Neither highlighting nor scroll-to-current applies to selection reads.

## Providers

- The rate limit fallback to one chunk at a time only lasts for the read in progress. Parallel generation is set per provider.
- **Auto-generate on open** costs money on every open of a missing or outdated note, with every provider.
- **ElevenLabs:** only the first **100 voices** on a provider's account are listed in a profile's voice dropdown. Eleven v3 is a research preview and can mispronounce or invent words, and Professional Voice Clones are not fully optimized for it yet.
- **OpenAI, Google Gemini and Amazon Polly** have fixed voice lists built into the plugin. A voice the service adds later isn't offered until a plugin update. Amazon Polly's custom Brand Voices aren't listed.
- **Google Gemini's** text to speech models are previews, and Google may change or replace them. Its part limit (5,000 characters) is a cautious choice, since Google documents none.
- **Amazon Polly:** some voices and engines are only offered in some regions. A voice the region doesn't have fails when you read.

## Platform

- Requires Obsidian 1.13.1 or newer.
- Requires an account with ElevenLabs, OpenAI, Google Gemini or Amazon Polly. No offline or local voice yet.

> [!question] Found something not listed?
> Open an issue on the [GitHub repository](https://github.com/pablokvitca/note-narrator).
