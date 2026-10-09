---
title: Background Generation
description: Generate a note's audio in the background without playing it, or move a read there, while you listen to or work on something else.
tags:
  - note-narrator
  - usage
  - background
publish: true
permalink: note-narrator/using/background-generation
plugin-version: 1.1.5
updated: 2026-10-09
---

# Background Generation

If you want a note's audio ready for later without listening to it now, generate it in the background. You can start it there directly, or move a read that is already going.

## Generate a note in the background

1. Open the note.
2. Click **Background** in the panel, or run the **Generate note audio in background** command.
3. The note joins the panel's **background jobs** list. Nothing stops or starts playing.

It always generates the whole note, even if you have text selected. If you close the note's tab, the panel's button still works: it generates the note as saved in your vault.

## Move a read to the background

While a note is reading and still has parts left to generate, the same button reads **Move to background**. Clicking it stops playback and keeps generating the rest of the note in the background, so you can come back to it later.

Selection reads stay where they are: they are never moved to the background. While a selection of the note is playing, the button generates the whole note in the background alongside it instead.

## The background jobs list

Each job shows as queued, generating or finished:

- **Queued** jobs wait their turn, numbered in the order you sent them. Background notes generate one at a time.
- The **generating** job shows how many parts are ready.
- **Finished** jobs are ready to play. You get a notice when one finishes, and the audio is saved and linked if saving is on (see [[Saving Audio]]).

Once a finished job's audio is saved to the vault, it is freed from memory, and clicking its card plays the saved file, the same as **Play saved**. Finished jobs that are *not* saved (saving is off, or the save failed) stay in memory. Up to **Unsaved finished notes kept in memory** of them are kept (5 by default, Performance tab): finishing one more clears the oldest from the list, with a notice. Playing a cleared note means generating it again.

A job whose note was edited after it was generated, or that was made with a different narrator than the one now selected, shows an **Outdated** badge. Hover it to see which. Playing it still plays the older version; open the note and select **Read** (or **Background**) to generate it again, which replaces the job.

Click a job to play it from the start. Pressing **Read** on a note that has a job does the same. The small button on a job either discards it (trash can, for a queued or generating job, throwing away its progress) or clears it with **Clear from list** (X, for a finished job).

![[background-jobs-list.png]]

## What the button says

The panel's background button follows the note you are viewing. Hover over it (or long-press on mobile) to see exactly what it will do:

| Button | Tooltip starts with | When |
| --- | --- | --- |
| **Background** | Generate in background | The note has no job and no up-to-date saved audio. Starts a new job |
| **Background** | Regenerate in background | The note's saved audio is up to date. Generates it again on purpose, like **Read** does |
| **Move to background** | | The note is being read and still has parts to generate |
| **Background** (disabled) | | The note is already queued or generating, or is playing from its saved audio |
| **Move to background** (disabled) | | The note's read has finished generating, so there is nothing to move |
| **Ready in background** (disabled) | | The note finished generating in the background. Play it from its card, or clear it from the list to generate it again |

The command makes the same decision and shows a notice when there is nothing to do.

> [!note] Edited notes
> If you change the note, or its narrator, after its job started, generating it in the background again replaces the old job with a fresh one.

## When files are deleted

- Deleting a note, or the audio file its finished job saved, removes its job from the list, so the note can be generated again.
- Deleting a note while it is being read lets the read finish playing, but its audio is not saved and it is never moved to the background.
- **Clear Note Narrator files** also clears a finished job from the list (the confirmation says so). A job that is still queued or generating is kept: its new audio is saved and linked when it finishes.

## Starting another note while one is still generating

With **Keep generating when starting another note** on (Performance tab, enabled by default), pressing **Read** or **Play saved** on a *different* note while one is still generating moves the note that was generating to the background first, the same as clicking **Move to background** yourself, instead of discarding its progress. It then starts the new note as usual.

This only applies when the note you're switching to is genuinely different. Reading the same note again (or one that already has a background job) adopts that job instead. A selection read is never moved: starting another note discards it.

Turn the setting off in [[Performance Settings]] to go back to the old behaviour, where starting another note discards whatever was generating.

## Separate concurrency

Background work has its own parallelism, **Max parallel background chunk generation** (default 1), set on the provider the note's narrator uses. It is low on purpose so it does not compete with a read you are actively listening to. See [[Providers Settings]].

## Display style

**Background job display** (in [[Appearance Settings]]) chooses how jobs look:

| Style | Look |
| --- | --- |
| **Minimal card** (default) | A small card with icon buttons |
| **Compact row** | A slim row with icon buttons |
| **Full callout** | A callout with text buttons per note |

All three play the note when you click anywhere on them except the buttons.
