---
title: Reading a Note
description: How to start a read, what text gets spoken, and how selections, titles, properties and comments are handled.
tags:
  - note-narrator
  - usage
publish: true
permalink: note-narrator/using/reading-a-note
plugin-version: 1.1.1
updated: 2026-10-06
---

# Reading a Note

## Starting a read

There are two ways, and they differ on purpose:

| Action | Opens panel | Starts reading |
| --- | --- | --- |
| Ribbon icon | Yes | No |
| Note toolbar icon | Yes | No |
| **Read** button in the panel | n/a | Yes |
| **Read note aloud** command | Yes | Yes |

> [!tip] Why opening does not read
> Reading costs credits, so simply looking at the panel never spends any. Only the Read button or the command does.

## What gets read

Before text goes to ElevenLabs, Markdown is cleaned up so it is not spoken literally: links, emphasis, code blocks, frontmatter and similar syntax are stripped.

In order, the spoken text can include:

1. **The note title**, if **Read note title** is on (default on), unless it exactly matches the note's first heading and **Skip title when it repeats the first heading** is on (default on), in which case the title is left out and only the heading is heard, once, as part of the body.
2. **The properties**, if **Read note properties** is on (default off). This says "Properties", then each key and value, then "Content".
3. **The note body**, minus anything you chose to skip.

The title and properties are spoken as part of the first part of the note, never as a part on their own, so playback flows straight into the note even when it starts with a heading.

> [!note] Selections
> With **Read selection instead of whole note** on (default on), an active text selection is read on its own, without the title or properties. Highlighting and scroll-to-current do not apply to selection reads.

## Skipping content

| Want to skip | Use |
| --- | --- |
| `%% Obsidian comments %%` | **Skip Markdown comments** (enabled by default) |
| Whole sections such as a Changelog | **Skip sections by heading**, one regex per line |
| Arbitrary regions | Not available yet, planned as "do not read aloud" delimiters. See [[Roadmap]] |

If you turn comment skipping off you can choose whether to hide the `%%` symbols and whether to announce comments as "Comment: ...". Details in [[General Settings]]. Each of these can also be overridden per narrator profile in [[Profiles Settings]].

> [!bug] HTML comments are still read
> `<!-- HTML comments -->` are not stripped and are read as literal text. An attempted fix did not hold up in testing. Tracked on the [[Roadmap]] and in [[Known Limitations]].

## Choosing a narrator for one read

Change the **Narrator** dropdown in the panel. It picks a narrator profile: a provider, a voice, and optional overrides of these reading settings. The profile chosen there stays active until you change it, and the **Default narrator** setting is the same thing. If the note already has saved audio made with different voice settings, the Read button becomes **Regenerate with new narrator**. See [[Profiles Settings]].
