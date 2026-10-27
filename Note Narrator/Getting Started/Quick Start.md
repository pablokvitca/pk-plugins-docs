---
title: Quick Start
description: Go from a fresh install to hearing your first note read aloud in five steps.
tags:
  - note-narrator
  - getting-started
publish: true
permalink: note-narrator/getting-started/quick-start
plugin-version: 1.2.0
updated: 2026-10-26
---

# Quick Start

From install to your first read.

## 1. Add a provider and its key

Open **Settings, Note Narrator, Providers**. A new install already has an **ElevenLabs** provider. To use another service, select **+** and choose **OpenAI**, **Google Gemini** or **Amazon Polly**.

![[settings-add-provider-menu.png]]

Open the provider and choose its key from Obsidian's secret storage (or create a new secret). Create the key first with only the permissions Note Narrator needs, a spending limit and an expiration date: follow [[Setting Up ElevenLabs]], [[Setting Up OpenAI]], [[Setting Up Google Gemini]] or [[Setting Up Amazon Polly]].

![[settings-provider-openai.png]]

## 2. Pick a voice and model

Open the **Profiles** tab. A new install has a **Default** profile for ElevenLabs, and adding a provider adds a **Default (provider name)** profile for it. Open the profile and choose a **Voice** and a **Model** (or **Engine** for Amazon Polly). The defaults work well for most notes. Select **Use as default narrator** to read with it. You can add more profiles later. See [[Profiles Settings]].

![[settings-profile-voice-openai.png]]

## 3. Open the panel

Click the **audio-lines** icon in the left ribbon, or the same icon in the top-right of a note's toolbar. This only opens the panel. It never starts reading by itself.

![[open-panel-ribbon-and-toolbar.png]]

## 4. Click Read

Open a note and press **Read** in the panel. Playback starts as soon as the first chunk is ready.

![[panel-reading.png]]

> [!tip] One step instead of two
> Run **Read note aloud** from the command palette to open the panel and start reading at once. See [[Commands]].

## 5. Optional: keep the audio

Turn on **Save generated audio to a file** and **Link saved audio in the note** to keep an audio file per note and replay it for free. See [[Saving Audio]].

> [!warning] Reading costs money
> Every generated chunk is charged by your provider: credits on your ElevenLabs plan, or OpenAI's, Google's or AWS's API prices. Saved audio plays back without spending any more.
