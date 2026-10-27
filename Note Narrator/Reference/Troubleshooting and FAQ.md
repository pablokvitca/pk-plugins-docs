---
title: Troubleshooting and FAQ
description: Answers to common problems and questions about Note Narrator.
tags:
  - note-narrator
  - reference
  - faq
publish: true
permalink: note-narrator/reference/troubleshooting
plugin-version: 1.2.0
updated: 2026-10-26
---

# Troubleshooting and FAQ

## Nothing happens when I click the icon

The icons only open the panel. Click **Read** in the panel, or run **Read note aloud**. See [[Reading a Note]].

## "Set the API key for the ... provider in the Note Narrator settings."

The provider your active narrator profile uses has no key yet ("Set the access keys" for Amazon Polly, which needs both keys and a region). Open **Settings, Note Narrator, Providers**, open that provider, and choose its key. Providers with no key show a warning marker. See [[Setting Up ElevenLabs]], [[Setting Up OpenAI]], [[Setting Up Google Gemini]] or [[Setting Up Amazon Polly]].

## A provider's request failed (401, 403 or similar)

The notice names the provider and starts with its answer. Usually the key is wrong, has expired, or lacks a permission Note Narrator needs, or (for Amazon Polly) the region or the user's policy doesn't allow `polly:SynthesizeSpeech`. Check the key against that provider's setup guide.

## "Add a provider and a narrator profile in the Note Narrator settings."

There is no usable narrator profile (for example after deleting the last provider). Add a provider on the **Providers** tab and a profile on the **Profiles** tab. See [[Providers Settings]].

## The voice dropdown is empty

For ElevenLabs, a narrator profile's **Voice** list comes from the provider's account. Set the provider's API key, then press the refresh button next to **Voice**. OpenAI, Google Gemini and Amazon Polly have fixed voice lists, so theirs are never empty (Amazon Polly lists the voices of the chosen **Engine**). See [[Profiles Settings]].

## A narrator is missing from the panel dropdown

Only profiles with **Show in panel dropdown** on appear, plus the active one. Turn it on in the profile's page. See [[Profiles Settings]].

## "ElevenLabs rate limit hit" (or OpenAI, Google Gemini, Amazon Polly)

You are making requests faster than your plan or quota allows. Note Narrator retries and switches to one chunk at a time. To avoid it, lower **Max parallel chunk generation** and **Max parallel background chunk generation** on the provider. See [[Providers Settings]].

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

**Does it work offline?** Not yet. Every provider so far is a cloud service. Local voices are planned. See [[Roadmap]].

**Does it work on mobile?** Yes. It has been tested on iPhone, iPad, iPad mini and visionOS. Android has not been tested. See [[Supported Platforms]].

**How much does it cost?** The plugin is free. Your provider charges for generated audio: credits on your ElevenLabs plan, or OpenAI's, Google's or AWS's API prices. Each setup guide links to its pricing page and shows how to set a spending limit. Saved audio replays for free.

**Can I use other voice providers?** Yes: ElevenLabs, OpenAI, Google Gemini and Amazon Polly, since 1.2.0. Add one with **+** under **Providers**, and you can add several of the same type, for example two accounts. Local voices are planned. See [[Providers Settings]] and [[Roadmap]].

**Can I rename the audio properties?** Yes, in [[Files Settings]].

**Why is a setting greyed out?** It depends on another setting that is off. For example the property names are greyed out until saving is on. Switch the setting it depends on back on. See [[Settings Overview]].

**Can different notes use different voices?** Yes: pick a narrator profile in the panel before reading. Choosing a profile automatically by folder is planned. See [[Roadmap]].
