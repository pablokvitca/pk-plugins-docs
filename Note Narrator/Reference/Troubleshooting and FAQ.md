---
title: Troubleshooting and FAQ
description: Answers to common problems and questions about Note Narrator.
tags:
  - note-narrator
  - reference
  - faq
publish: true
permalink: note-narrator/reference/troubleshooting
plugin-version: 1.1.6
updated: 2026-10-26
---

# Troubleshooting and FAQ

## Nothing happens when I click the icon

The icons only open the panel. Click **Read** in the panel, or run **Read note aloud**. See [[Reading a Note]].

## "Set an API key for the ... provider in the Note Narrator settings."

The provider your active narrator profile uses has no API key yet. Open **Settings, Note Narrator, Providers**, open that provider, and choose an API key. Providers with no key show a warning marker. See [[Setting Up ElevenLabs]].

## "Add a provider and a narrator profile in the Note Narrator settings."

There is no usable narrator profile (for example after deleting the last provider). Add a provider on the **Providers** tab and a profile on the **Profiles** tab. See [[Providers Settings]].

## The voice dropdown is empty

In a narrator profile, the **Voice** list comes from its provider's account. Set the provider's API key, then press the refresh button next to **Voice**. See [[Profiles Settings]].

## A narrator is missing from the panel dropdown

Only profiles with **Show in panel dropdown** on appear, plus the active one. Turn it on in the profile's page. See [[Profiles Settings]].

## "ElevenLabs rate limit hit"

You are making requests faster than your plan allows. Note Narrator retries and switches to one chunk at a time. To avoid it, lower **Max parallel chunk generation** and **Max parallel background chunk generation** on the provider. See [[Providers Settings]].

## Highlighting does not show

Highlighting needs the note open in **Editing view**, and **Highlight while reading** turned on. It does not work in Reading view or for selection reads. See [[Highlighting and Scrolling]].

## It says "Saved audio is outdated" but I only changed a little

Any change to the note's text, anywhere, marks audio outdated. Property edits only count with **Read note properties** on (or for audio saved before 1.1.6, until it's regenerated). With it on, exclude noisy properties with **Extra properties to exclude from staleness hashing**. See [[Saving Audio]].

## Previous and Next part do not work during Play saved

Either the note is outdated, or a chunk-affecting setting changed since the audio was made, so the file plays as one piece. Regenerate. See [[Known Limitations]].

## "Cleaned up stale Note Narrator audio file metadata properties"

A note linked to an audio file that no longer exists, so the leftover properties were removed. Turn this off with **Auto-clean up properties when saved file is missing**.

## It reads symbols like `<!--`

HTML comments are read as text. See [[Known Limitations]].

## FAQ

**Does it work offline?** Not yet. It needs ElevenLabs. Local voices are planned. See [[Roadmap]].

**Does it work on mobile?** Yes. It has been tested on iPhone, iPad, iPad mini and visionOS. Android has not been tested. See [[Supported Platforms]].

**How much does it cost?** The plugin is free. ElevenLabs charges credits for generated audio. Saved audio replays for free.

**Can I use other voice providers?** Not yet. Providers have a type, and only ElevenLabs is implemented, so other services can be added later. You can already add several ElevenLabs providers, for example two accounts. See [[Providers Settings]] and [[Roadmap]].

**Can I rename the audio properties?** Yes, in [[Files Settings]].

**Why is a setting greyed out?** It depends on another setting that is off. For example the property names are greyed out until saving is on. Switch the setting it depends on back on. See [[Settings Overview]].

**Can different notes use different voices?** Yes: pick a narrator profile in the panel before reading. Choosing a profile automatically by folder is planned. See [[Roadmap]].
