---
title: Long Notes and Chunking
description: How long notes are split into chunks, quick start, parallel generation and rate limit handling.
tags:
  - note-narrator
  - usage
  - performance
publish: true
permalink: note-narrator/using/long-notes-and-chunking
plugin-version: 1.2.0
updated: 2026-10-26
---

# Long Notes and Chunking

Every provider limits how much text one request can hold, so Note Narrator splits a note into **chunks**, generates them, and plays them in order. The limit depends on the provider, and for ElevenLabs on the model: see the table on [[Providers Settings#Character limits]].

## Text chunker

| Style | How it splits |
| --- | --- |
| **Markdown-aware** (default) | By heading section first (up to the max heading depth), then by sentence inside each section |
| **Sentence-only** | Ignores headings and packs sentences up to the character limit |

**Max heading depth** (default 2, and overridable per narrator profile) decides which headings start a new section: 1 is `#`, 2 is `##` and shallower, up to 6. Deeper headings stay inside their section.

> [!example] Skipping a section
> With the Markdown-aware chunker, add `Changelog` to **Skip sections by heading** and any section whose heading matches is never read, so its parts also disappear from the generation bar.

## Start playing sooner

- **Start playback immediately** (enabled by default): play as soon as the first chunk is ready instead of waiting for the whole note.
- **Quick start** (enabled by default): make that first chunk deliberately short (including the title and properties preamble) so audio starts faster. Size it in **Words** (default 150) or **Characters** (default 750).

> [!tip] Long notes
> Quick start matters most on long notes. The first sentence or two are generated alone, and everything else generates while you listen.

## Parallel generation

- **Generate chunks in parallel** (enabled by default): more than one chunk at a time. **Max parallel chunk generation** sets the window (default 2, recommended 2 to 5). Both are set **per provider**, because rate limits belong to the account. See [[Providers Settings]].
- More parallelism finishes long notes sooner, but makes more simultaneous requests and hits rate limits sooner.

> [!warning] Rate limits
> When the provider rate-limits a request, it's retried with a growing, slightly random wait, and generation falls back to one chunk at a time for the **rest of that read**. Each new read starts again at your configured parallelism.
>
> | Provider | Rate limited when | Retries | Longest wait |
> | --- | --- | --- | --- |
> | ElevenLabs | HTTP 429 | 8 | 30 seconds |
> | OpenAI | HTTP 429. Waits as long as OpenAI asks, when it says | 6 | 20 seconds |
> | Google Gemini | HTTP 429. Waits as long as Google asks, when it says | 6 | 60 seconds |
> | Amazon Polly | HTTP 429, or a 400 that says it's throttling | 6 | 15 seconds |

## Saved audio and chunks

Saved audio remembers its own chunk boundaries so Previous/Next part and highlighting keep working during Play saved. If chunk-affecting settings changed since generation, the file plays as one non-navigable piece until you regenerate. See [[Saving Audio]] and [[Known Limitations]].
