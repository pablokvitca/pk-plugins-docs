---
title: Note Narrator
description: Note Narrator reads your Obsidian notes aloud with ElevenLabs text to speech. Documentation, setup, settings reference and roadmap.
tags:
  - note-narrator
  - docs
aliases:
  - Note Narrator docs
publish: true
permalink: note-narrator
plugin-version: 1.1.0
updated: 2026-10-05
---

# Note Narrator

> [!info] Part of PK Plugins
> This is the documentation for one plugin. See [[index|PK Plugins]] for the rest.

Note Narrator is an Obsidian plugin that **reads your notes aloud** using text to speech. It ships with [ElevenLabs](https://elevenlabs.io) as its voice provider, plays audio while it is still being generated, and can save the result as an `.mp3` linked from the note.

> [!tip] New here?
> Start with [[Installation]], then follow the [[Quick Start]]. You will be listening to a note in a few minutes.

![[hero-panel-and-note.png]]

## What it does

- Reads the whole note, or just your selection, with a narrator profile: a provider, a voice, and your own reading settings.
- Starts playing after the first short chunk is ready, and keeps generating the rest while you listen. See [[Long Notes and Chunking]].
- Saves audio to your vault and tracks whether it is still up to date. See [[Saving Audio]].
- Highlights what is being read and scrolls the note to it. See [[Highlighting and Scrolling]].
- Generates notes in the background without playing them, ready to listen to later. See [[Background Generation]].

## Documentation map

### Getting started
- [[Installation]]: BRAT, manual install, requirements
- [[Quick Start]]: from install to your first read
- [[Setting Up ElevenLabs]]: API key, voices and models
- [[Providers Settings]] and [[Profiles Settings]]: how providers and narrator profiles fit together

### Using Note Narrator
- [[The Panel]]: every part of the sidebar panel
- [[Reading a Note]]: what gets read and how to start
- [[Playback Controls]]
- [[Long Notes and Chunking]]
- [[Saving Audio]]
- [[Highlighting and Scrolling]]
- [[Background Generation]]
- [[Commands]]

### Settings
- [[Settings Overview]] links to one page per settings tab:
  [[General Settings]], [[Providers Settings]], [[Profiles Settings]], [[Appearance Settings]], [[Performance Settings]], [[Files Settings]]

### Reference
- [[Frontmatter Properties]]
- [[Supported Platforms]]: what has been tested where
- [[Known Limitations]]
- [[Privacy and Network Use]]
- [[Troubleshooting and FAQ]]

### Roadmap
- [[Roadmap]]: what is next and what is being considered

> [!info] About this documentation
> These docs describe version **1.1**. If you are on 0.16.x, the settings screen looks different from these pages -- 0.17 reorganised it around providers and narrator profiles. Something wrong or missing? Open an issue on the [GitHub repository](https://github.com/pablokvitca/note-narrator).

> [!note] Independent project
> Note Narrator is an independent project. It is not affiliated with, endorsed by, or sponsored by Obsidian or ElevenLabs. "Obsidian" and "ElevenLabs" are trademarks of their respective owners and are used here only to describe what the plugin works with. See [[Privacy and Network Use]] for how your data is handled.
