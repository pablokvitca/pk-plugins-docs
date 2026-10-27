---
title: Highlighting and Scrolling
description: Follow along in the editor with a margin marker, background or underline highlight, and the scroll to current section button.
tags:
  - note-narrator
  - usage
  - highlighting
publish: true
permalink: note-narrator/using/highlighting-and-scrolling
plugin-version: 1.2.0
updated: 2026-10-26
---

# Highlighting and Scrolling

## Highlight while reading

Disabled by default. When on, the text being read is marked in the editor as it plays.

> [!important] Editing view only
> Highlighting draws into the editor, so the note must be open in **Editing view** (Live Preview or Source). Reading view has nothing to draw onto.

### Granularity

| Granularity | Moves |
| --- | --- |
| **Chunk** (default) | Once per generated audio request |
| **Section** | Least often. With the sentence-only chunker there are no sections, so the whole note lights up |

Both are exact because they follow which chunk is really playing. With Section granularity, **Only highlight the section heading** narrows it to the heading line.

### Style

| Style | Look |
| --- | --- |
| **Margin marker** (default) | A small speaker icon in the left gutter, where line numbers go. Text is untouched |
| **Background wash** | Colours the text background |
| **Underline** | Underlines the text |

**Margin marker**

![[highlight-margin-marker.png]]

**Background wash**

![[highlight-background.png]]

**Underline**

![[highlight-underline.png]]

## Scroll to current section

The **Scroll to current section** button (enabled by default) sits at the end of the playback controls. It scrolls to, and selects, whichever section is playing. It works whether or not highlighting is on, and never affects playback. It is called "scroll", not "jump", because it only moves the editor.

It works per section, not per chunk, because a chunk is an internal request boundary, not something you navigate by.

## During Play saved

Both features also work during **Play saved**, as long as the note is up to date with the audio. See [[Saving Audio]].

## Limits

> [!note] Not for selections
> Neither feature applies when you read a selection.

> [!caution] Positions are estimates
> Mapping chunk and section positions back to the raw note is proportional, because Markdown stripping changes text length. A boundary can be off by a word or two. A comment containing heading-like text (`# ...`) can also confuse section boundaries.

> [!info] Sentence and word highlighting
> Not available yet. They would need word timing from the provider, and an early estimate-based version drifted out of sync in testing and was removed. See [[Roadmap]].
