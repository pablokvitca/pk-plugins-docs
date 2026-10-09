---
title: Frontmatter Properties
description: The frontmatter properties Note Narrator writes to notes with saved audio and what each is for.
tags:
  - note-narrator
  - reference
  - saved-audio
publish: true
permalink: note-narrator/reference/frontmatter-properties
plugin-version: 1.1.4
updated: 2026-10-08
---

# Frontmatter Properties

When **Link saved audio in the note** is on, Note Narrator writes six properties to the note. All names are configurable in [[Files Settings]]. These are the defaults.

| Property | Contains |
| --- | --- |
| `note_narrator_audio` | A wikilink to the saved `.mp3`, so Obsidian shows and tracks it |
| `note_narrator_audio_hash` | Hash of the note's content when the audio was made, used for [[Saving Audio#Linking and staleness\|staleness]] |
| `note_narrator_audio_path` | Raw vault path of the file, used internally. Only an `.mp3` path counts: anything else is treated as no saved audio |
| `note_narrator_audio_timestamp` | When the audio was generated |
| `note_narrator_audio_voice` | A fingerprint (hash) of the narrator profile's voice settings that made the audio. Notes saved before 0.17 hold the raw ElevenLabs voice ID here, which still counts as a match for that voice |
| `note_narrator_audio_chunk_durations` | A list of `[duration in seconds, byte length]` pairs, one per chunk |

## Example

```yaml
---
note_narrator_audio: "[[My Note (Rachel).mp3]]"
note_narrator_audio_hash: 4ac88baf
note_narrator_audio_path: Notes/My Note (Rachel).mp3
note_narrator_audio_timestamp: 2026-09-12T16:24:48.902-04:00
note_narrator_audio_voice: 9c1f03ab
note_narrator_audio_chunk_durations:
  - - 33.11
    - 530852
  - - 9.06
    - 145911
---
```

> [!info] What the voice fingerprint covers
> The provider type, voice, model, stability and similarity boost. Renaming a profile, moving it to another account, or changing its reading overrides does not change it. If the selected profile's fingerprint differs from a note's, the Read button becomes **Regenerate with new narrator**. See [[Profiles Settings]].

> [!note] They are excluded from the hash
> Note Narrator's own six properties never count as an edit, so writing them does not make the audio look outdated.

> [!info] Editing by hand
> Do not edit these by hand. Removing them detaches the note from its audio. Use **Clear Note Narrator files** to do it properly.

> [!tip] Hiding them
> The properties show in Obsidian's Properties view. A setting to hide them is on the [[Roadmap]].
