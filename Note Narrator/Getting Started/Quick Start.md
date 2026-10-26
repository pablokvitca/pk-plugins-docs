---
title: Quick Start
description: Go from a fresh install to hearing your first note read aloud in five steps.
tags:
  - note-narrator
  - getting-started
publish: true
permalink: note-narrator/getting-started/quick-start
plugin-version: 1.1.6
updated: 2026-10-26
---

# Quick Start

From install to your first read.

## 1. Add your ElevenLabs API key

Open **Settings, Note Narrator, Providers**, open the **ElevenLabs** provider, and choose your API key from Obsidian's secret storage (or create a new secret). Full detail in [[Setting Up ElevenLabs]].

![[settings-api-key.png]]

## 2. Pick a voice and model

Open the **Profiles** tab and the **Default** narrator profile. Choose a **Voice** (fetched from your account) and a **Model**. The defaults work well for most notes: Eleven Multilingual v2 is a solid balance of quality and cost. You can add more profiles later. See [[Profiles Settings]].

## 3. Open the panel

Click the **audio-lines** icon in the left ribbon, or the same icon in the top-right of a note's toolbar. This only opens the panel. It never starts reading by itself.

![[open-panel-ribbon-and-toolbar.png]]

## 4. Click Read

Open a note and press **Read** in the panel. Playback starts as soon as the first chunk is ready.

![[panel-reading.png]]

> [!tip] One step instead of two
> Run **Read note aloud** from the command palette to open the panel and start reading at once. See [[Commands]].

## 5. Optional: keep the audio

Turn on **Save generated audio to a file** and **Link saved audio in the note** to keep an `.mp3` per note and replay it for free. See [[Saving Audio]].

> [!warning] Reading uses ElevenLabs credits
> Every generated chunk costs credits on your ElevenLabs plan. Saved audio plays back without spending any more.
