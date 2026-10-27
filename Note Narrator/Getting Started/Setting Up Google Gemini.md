---
title: Setting Up Google Gemini
description: Create a Gemini API key restricted to the Gemini API, cap the project's monthly spend, rotate the key, and choose a voice and model.
tags:
  - note-narrator
  - getting-started
  - gemini
publish: true
permalink: note-narrator/getting-started/setting-up-google-gemini
plugin-version: 1.2.0
updated: 2026-10-26
---

# Setting Up Google Gemini

Note Narrator can generate speech with Google's Gemini text to speech models (preview). You need a Google AI Studio account and a Gemini API key. On a paid tier, Google charges for the audio at its API prices. On the free tier, Google may use what you send to improve its products.

> [!warning] Keep the key limited
> Note Narrator only needs the Gemini API. Keep the key **restricted to the Gemini API**, put it in a project with a **monthly spend cap**, and **replace it regularly**, since Gemini keys can't be given an expiration date. Don't use an unrestricted Google Cloud key, or a project without a spend cap: if it leaks, anyone can spend on your account until you notice.

## 1. A project with a spend cap

1. Sign in at [Google AI Studio](https://aistudio.google.com) and create a project for Note Narrator (or import a Google Cloud project you only use for it).
2. If you want the paid tier, set up billing for it.
3. On the project's **Spend** page, under **Monthly spend cap**, select **Edit spend cap** and set the most you would be comfortable losing in a month. You need to be the project's editor, owner or admin.

Google notes that spend is processed with a delay of up to about 10 minutes, so it can go past the cap. Separately, every billing account has a monthly cap for its tier, and reaching it pauses the Gemini API for all its projects until the next month. See Google's [billing documentation](https://ai.google.dev/gemini-api/docs/billing).

## 2. A key restricted to the Gemini API

1. Open the [API Keys page](https://aistudio.google.com/apikey) and create a key in your Note Narrator project.
2. Check it shows as restricted to the Gemini API. New AI Studio keys are, by default. If a key shows **Unrestricted**, hover over that label, select **Add restrictions**, and restrict it to the Gemini API.
3. Copy the key.

Don't reuse a Google Cloud key that can call other Google APIs. See Google's [API key documentation](https://ai.google.dev/gemini-api/docs/api-key).

> [!info] No expiration date
> Gemini API keys don't have an expiration setting. Instead, set yourself a reminder to replace the key, for example every three months: create a new key, paste it into the same secret in Obsidian, check a read works, then delete the old key in AI Studio. Delete a key straight away if you think it leaked.

## 3. Add it to Note Narrator

1. In Obsidian, open **Settings, Note Narrator, Providers**, select **+** and choose **Google Gemini** (or switch an existing provider's **Type** to Google Gemini).

   ![[settings-add-provider-menu.png]]

2. Open the new provider. Under **API key**, pick an existing secret or create a new one and paste the key. The **Setting up Google Gemini keys safely** link under it opens this guide.

   ![[settings-provider-google-gemini.png]]

> [!info] Where the key lives
> The key is stored with Obsidian's [secret storage](https://docs.obsidian.md/plugins/guides/secret-storage), not in the plugin's `data.json`. Only the secret's name is saved (`gemini-api-key` by default).

## 4. Set up a narrator profile

Adding the provider also added a narrator profile for it, named **Default (Google Gemini)**, so you can read with it straight away.

1. Open **Settings, Note Narrator, Profiles** and select **Default (Google Gemini)** (or add a profile with **+** and set its **Provider** to this one).
2. Under **Voice**, choose a voice and the other settings below.
3. Select **Use as default narrator**, or pick the profile in the panel's narrator dropdown.

![[settings-profile-voice-google-gemini.png]]

## Voices, models and settings

A narrator profile using Gemini has:

| Setting | What it does |
| --- | --- |
| **Voice** | One of Gemini's 30 prebuilt voices. Kore by default |
| **Model** | **Gemini 2.5 Flash TTS** (default) or **Gemini 2.5 Pro TTS**, both previews |
| **Instructions** | Optional guidance on tone and delivery, such as "Say in a calm, warm voice", read by the model before each part |

Each part of a note is at most 5,000 characters. Gemini's audio is saved as a `.wav` file, which is larger than an `.mp3`. If Gemini rate-limits a request, Note Narrator waits as long as Google asks and retries. See [[Providers Settings]], [[Profiles Settings]] and [[Saving Audio]].

> [!info] What is sent
> The text being read, the voice and model settings, and your key go to Google (`generativelanguage.googleapis.com`), under the Gemini API terms. See [[Privacy and Network Use]].

## Official links

Google's own pages, for anything this guide doesn't cover or that has changed since.

**Documentation**
- [Speech generation](https://ai.google.dev/gemini-api/docs/speech-generation): the text to speech models, voices and prompts Note Narrator uses
- [API keys](https://ai.google.dev/gemini-api/docs/api-key): creating and restricting keys
- [Billing](https://ai.google.dev/gemini-api/docs/billing): tiers, the billing account cap and project spend caps
- [Rate limits](https://ai.google.dev/gemini-api/docs/rate-limits)

**Terms and policies**
- [Gemini API Additional Terms of Service](https://ai.google.dev/gemini-api/terms): including how free-tier data is used
- [Google Privacy Policy](https://policies.google.com/privacy)
- [Generative AI Prohibited Use Policy](https://policies.google.com/terms/generative-ai/use-policy)

**Pricing and billing**
- [Gemini API pricing](https://ai.google.dev/gemini-api/docs/pricing): what the text to speech models cost, and what the free tier includes
- [Spend](https://aistudio.google.com/spend): your project's spend and its monthly spend cap
- [Usage](https://aistudio.google.com/usage): requests and limits so far
