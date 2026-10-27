---
title: Privacy and Network Use
description: What data Note Narrator sends over the network, to whom, and what it stores.
tags:
  - note-narrator
  - reference
  - privacy
publish: true
permalink: note-narrator/reference/privacy
plugin-version: 1.2.0
updated: 2026-10-26
---

# Privacy and Network Use

Note Narrator does not collect telemetry or analytics, and it never runs remote code.

## What is sent, and when

> [!important] Only the providers you set up
> Note Narrator talks only to the provider of the narrator profile you read with, and only when you trigger a read, regenerate, generate in the background, or (if enabled) auto-generate on open. For ElevenLabs, also when you load your voice list.

| Provider | Where requests go |
| --- | --- |
| ElevenLabs | `api.elevenlabs.io` |
| OpenAI | `api.openai.com` |
| Google Gemini | `generativelanguage.googleapis.com` |
| Amazon Polly | `polly.<region>.amazonaws.com`, in the region you chose for the provider |

| Request | Data sent |
| --- | --- |
| Generate speech (every provider) | The text being read (after Markdown cleanup), the narrator profile's voice, model and voice settings, and the provider's key. Amazon Polly requests are signed with your access keys instead: the secret access key itself is never sent |
| List voices (ElevenLabs only) | The provider's API key, to fetch that account's voices (when you open a profile's page or press refresh) |
| Name a saved audio file (ElevenLabs only) | The provider's API key and the voice ID, to label the file with the voice's name (each time audio is saved). The other providers' voices are fixed lists, named without asking |

Requests a provider rate-limits are retried automatically and resend the same text, which can cost more.

The text of a note leaves your device when you read it. If a note is sensitive, do not read it with this plugin. Your provider's own terms and privacy policy apply to what it receives. On Google Gemini's free tier, Google may use what you send to improve its products.

## What is stored

- **API keys and AWS access keys:** in Obsidian's secret storage, not in the vault or plugin settings. Only the name of each provider's secrets is saved (and Amazon Polly's region, which isn't secret).
- **Settings:** in the plugin's `data.json`.
- **Audio and tracking data:** `.mp3` files (`.wav` with Google Gemini) in your vault and frontmatter properties on notes. See [[Frontmatter Properties]].

Nothing is sent to the plugin author.

## Other notes it looks at

Note Narrator reads only the note you're reading, with one exception. Before it replaces or trashes a note's saved audio, it checks whether another note links the same audio file, so a copied note (which keeps the original's properties) doesn't overwrite or trash audio the original still uses.

- **What it reads:** each note's Note Narrator audio path property, from Obsidian's metadata cache. It never reads the notes' text.
- **When:** only when it saves audio in **Replace existing file** mode for a note that already has audio, and when you clear a note's audio.
- **Where it goes:** nowhere. Nothing it sees leaves your device.

The check lists every note in your vault, which is why Obsidian's plugin scanner reports "vault enumeration". It's on by default. Turn it off with **Protect audio shared with copied notes** in [[Files Settings]]. With it off, regenerating or clearing a copied note can overwrite or trash the original's audio.

> [!tip] Keep audio out of sync targets
> If your vault syncs, saved audio files sync with it and can be large, `.wav` files especially. Choose a folder you can exclude from sync under **Save location**. Saving outside the vault is planned. See [[Roadmap]].

## Your provider's terms apply to you

Note Narrator only sends requests to your provider on your behalf. Your account and the audio it produces are covered by that provider's own terms and policies:

| Provider | Terms | Privacy | Usage rules |
| --- | --- | --- | --- |
| ElevenLabs | [Terms of Service](https://elevenlabs.io/terms-of-use) | [Privacy Policy](https://elevenlabs.io/privacy-policy) | [Prohibited Use Policy](https://elevenlabs.io/use-policy) |
| OpenAI | [Services Agreement](https://openai.com/policies/services-agreement) | [Privacy Policy](https://openai.com/policies/privacy-policy) | [Usage Policies](https://openai.com/policies/usage-policies) |
| Google Gemini | [Gemini API Additional Terms](https://ai.google.dev/gemini-api/terms) | [Privacy Policy](https://policies.google.com/privacy) | [Generative AI Prohibited Use Policy](https://policies.google.com/terms/generative-ai/use-policy) |
| Amazon Polly | [AWS Customer Agreement](https://aws.amazon.com/agreement/) and [Service Terms](https://aws.amazon.com/service-terms/) | [Privacy Notice](https://aws.amazon.com/privacy/) | [Acceptable Use Policy](https://aws.amazon.com/aup/) |

For ElevenLabs in particular:

- **Who can use it:** ElevenLabs' [Terms of Service](https://elevenlabs.io/terms-of-use) say you must be 18 or over (or of legal age where you live) to use its services.
- **What you may do with the audio:** the terms allow free accounts to use the service for non-commercial purposes only, and paid plans for commercial purposes. Check your plan before using saved audio commercially.
- **What you may read:** you need the rights to any text you send, and your use must follow ElevenLabs' [Prohibited Use Policy](https://elevenlabs.io/use-policy).
- **AI-generated audio:** if you share it, consider saying it is AI-generated.
- **Your API key:** it is yours alone. Do not share it or use it to resell access.

> [!note] Not legal advice
> These are summaries, and providers can change their terms. The terms on their sites are the ones that count.

