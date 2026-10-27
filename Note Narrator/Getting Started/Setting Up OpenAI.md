---
title: Setting Up OpenAI
description: Create a restricted, expiring OpenAI API key in a project with a hard spend limit, store it safely in Obsidian, and choose a voice and model.
tags:
  - note-narrator
  - getting-started
  - openai
publish: true
permalink: note-narrator/getting-started/setting-up-openai
plugin-version: 1.2.0
updated: 2026-10-26
---

# Setting Up OpenAI

Note Narrator can generate speech with OpenAI's text to speech models. You need an OpenAI API account with billing set up, and an API key. OpenAI charges for the audio it generates, at its API prices.

> [!warning] Keep the key limited
> Note Narrator only needs to turn text into speech. Give the key **only that permission**, put it in a project with a **hard spend limit**, and give it an **expiration date**. Don't create a key with all permissions, a project without a spend limit, or a key that never expires: if it leaks, anyone can spend on your account until you notice.

## 1. A project with a spend limit

Keys belong to a project, and limits are set per project, so give Note Narrator its own.

1. Sign in at [platform.openai.com](https://platform.openai.com) and create a project, for example "Note Narrator".
2. In the project's settings, open **Limits** and set a **hard spend limit** for the month. When the project's spending reaches it, OpenAI stops its requests until the next month, so pick the most you would be comfortable losing.
3. Also set a **spend alert** below that, to get an email before you reach it.

OpenAI notes that spending is tracked with a short delay, so it can go slightly past the limit.

## 2. A restricted key with an expiration date

1. In the project, open **API keys** and create a new secret key, owned by you or by a service account.
2. Name it, for example "Note Narrator".
3. Set **Permissions** to **Restricted**, and allow only the model `Request`s. Note Narrator makes (the **Model capabilities** group, which includes text to speech at `/v1/audio/speech`). Leave everything else at **None**.
4. Set an **expiration date**. OpenAI recommends one for every project key. A few months is a reasonable start.
5. Create the key and copy it: OpenAI shows it only once.

If reads fail with a "missing scope" error, the key is missing the text to speech permission: edit it and allow model requests in **Model capabilities**. OpenAI's labels can change: see their [production best practices](https://developers.openai.com/api/docs/guides/production-best-practices) for the current options.

## 3. Add it to Note Narrator

1. In Obsidian, open **Settings, Note Narrator, Providers**, select **+** and choose **OpenAI** (or switch an existing provider's **Type** to OpenAI).

   ![[settings-add-provider-menu.png]]

2. Open the new provider. Under **API key**, pick an existing secret or create a new one and paste the key. The **Setting up OpenAI keys safely** link under it opens this guide.

   ![[settings-provider-openai.png]]

> [!info] Where the key lives
> The key is stored with Obsidian's [secret storage](https://docs.obsidian.md/plugins/guides/secret-storage), not in the plugin's `data.json`. Only the secret's name is saved (`openai-api-key` by default).

When the key expires, reads fail with an authentication error. Create a new key the same way and paste it into the same secret.

## 4. Set up a narrator profile

Adding the provider also added a narrator profile for it, named **Default (OpenAI)**, so you can read with it straight away.

1. Open **Settings, Note Narrator, Profiles** and select **Default (OpenAI)** (or add a profile with **+** and set its **Provider** to this one).
2. Under **Voice**, choose a voice and the other settings below.
3. Select **Use as default narrator**, or pick the profile in the panel's narrator dropdown.

![[settings-profile-voice-openai.png]]

## Voices, models and settings

A narrator profile using OpenAI has:

| Setting | What it does |
| --- | --- |
| **Voice** | One of OpenAI's 13 built-in voices. Alloy by default |
| **Model** | **GPT-4o mini TTS** (default), **TTS-1** (faster) or **TTS-1 HD** (higher quality) |
| **Speaking speed** | How fast the voice speaks, set when the audio is generated (0.25 to 4, default 1) |
| **Instructions** | Optional guidance on tone, accent or pacing. Only GPT-4o mini TTS uses it |

Each part of a note is at most 4,096 characters. If OpenAI rate-limits a request, Note Narrator waits as long as OpenAI asks and retries. See [[Providers Settings]] and [[Profiles Settings]].

> [!info] What is sent
> The text being read, the voice and model settings, and your key go to OpenAI (`api.openai.com`), under OpenAI's terms and privacy policy. See [[Privacy and Network Use]].

## Official links

OpenAI's own pages, for anything this guide doesn't cover or that has changed since.

**Documentation**
- [Text to speech guide](https://developers.openai.com/api/docs/guides/text-to-speech): models, voices and instructions
- [Create speech API](https://developers.openai.com/api/reference/resources/audio/subresources/speech/methods/create): what Note Narrator calls to generate audio
- [Production best practices](https://developers.openai.com/api/docs/guides/production-best-practices): key expiration, spend alerts and hard spend limits
- [Managing projects](https://help.openai.com/en/articles/9186755-managing-projects-in-the-api-platform) and [API key permissions](https://help.openai.com/en/articles/8867743-assign-api-key-permissions)
- [Rate limits](https://developers.openai.com/api/docs/guides/rate-limits)

**Terms and policies**
- [Services Agreement](https://openai.com/policies/services-agreement) (applies to the API) and [Terms of Use](https://openai.com/policies/terms-of-use)
- [Privacy Policy](https://openai.com/policies/privacy-policy)
- [Usage Policies](https://openai.com/policies/usage-policies)

**Pricing and billing**
- [API pricing](https://openai.com/api/pricing) and the [pricing reference](https://developers.openai.com/api/docs/pricing): what text to speech costs per model
- [Billing](https://platform.openai.com/settings/organization/billing/overview): payment method and credit balance
- [Usage](https://platform.openai.com/usage): what you have spent so far, per project
