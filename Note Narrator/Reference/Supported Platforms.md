---
title: Supported Platforms
description: Which Obsidian platforms Note Narrator supports, and how well each one has been tested.
tags:
  - note-narrator
  - reference
  - platforms
publish: true
permalink: note-narrator/reference/supported-platforms
plugin-version: 1.2.0
updated: 2026-10-26
---

# Supported Platforms

Note Narrator is not desktop-only, so Obsidian will load it on every platform. That does not mean every platform has been tried. This page says which have.

## Support levels

Two things vary by platform: whether Note Narrator has been tried there, and which text to speech provider you can use with it.

| Testing level | Meaning |
| --- | --- |
| ✅ **Tested** | Used on a real device and works as expected |
| ❔ **Not tested** | Should work, since the plugin uses only Obsidian's cross-platform APIs, but nobody has tried it. Reports welcome |
| ⛔ **Unsupported** | Known not to work, or not meant to work |

| Provider level | Meaning |
| --- | --- |
| ✅ **Supported** | Available in the current version |
| 🔜 **Upcoming** | Planned, not available yet. See the [[Roadmap]] |
| ➖ **Not applicable** | The provider cannot exist on that platform |

## Platforms

| Platform | Testing | ElevenLabs | OpenAI | Google Gemini | Amazon Polly | Apple OS (Local) |
| --- | --- | --- | --- | --- | --- | --- |
| macOS | ✅ Tested | ✅ Supported | ✅ Supported | ✅ Supported | ✅ Supported | 🔜 Upcoming |
| iPhone (iOS) | ✅ Tested | ✅ Supported | ✅ Supported | ✅ Supported | ✅ Supported | 🔜 Upcoming |
| iPad (iPadOS) | ✅ Tested | ✅ Supported | ✅ Supported | ✅ Supported | ✅ Supported | 🔜 Upcoming |
| iPad mini (iPadOS) | ✅ Tested | ✅ Supported | ✅ Supported | ✅ Supported | ✅ Supported | 🔜 Upcoming |
| Apple Vision Pro (visionOS) | ✅ Tested | ✅ Supported | ✅ Supported | ✅ Supported | ✅ Supported | 🔜 Upcoming |
| Windows | ❔ Not tested | ✅ Supported | ✅ Supported | ✅ Supported | ✅ Supported | ➖ Not applicable |
| Linux | ❔ Not tested | ✅ Supported | ✅ Supported | ✅ Supported | ✅ Supported | ➖ Not applicable |
| Android phone and tablet | ❔ Not tested | ✅ Supported | ✅ Supported | ✅ Supported | ✅ Supported | ➖ Not applicable |

- **ElevenLabs**, **OpenAI**, **Google Gemini** and **Amazon Polly** are cloud providers: each needs an internet connection and an account with that service. See [[Setting Up ElevenLabs]], [[Setting Up OpenAI]], [[Setting Up Google Gemini]] and [[Setting Up Amazon Polly]].
- OpenAI, Google Gemini and Amazon Polly were added in 1.2.0 and have been tested on macOS, iPhone and iPad. ElevenLabs has been tested on every platform marked **Tested**.
- **Apple OS (Local)** will use the text to speech built into Apple's operating systems, with no network or account, so it only applies to Apple platforms.
- VisionOS runs the iPad version of Obsidian. There is no Obsidian web app, so a browser is not a supported platform.

> [!info] iOS below 16.4
> Regular expression lookbehind is not available on iOS and iPadOS before 16.4. Note Narrator itself does not use lookbehind, but a lookbehind pattern you type in **Skip sections by heading** may be ignored there. See [[General Settings]].

## Obsidian versions

| Obsidian version | Support |
| --- | --- |
| 1.13.1 and newer | ✅ Tested |
| 1.13.0 and older | ⛔ Unsupported. The settings screen needs APIs added in 1.13.1 |

> [!tip] Help fill in the gaps
> If you use Note Narrator on a platform marked **Not tested**, tell us whether it works by opening an issue on the [GitHub repository](https://github.com/pablokvitca/note-narrator). Include your platform and Obsidian version.

See also [[Installation]], [[Known Limitations]] and [[Troubleshooting and FAQ]].
