# MoneyPrinterTurbo — Android / Colab Workflow Progress

Updated: 10 November 2026

## Goal

Produce a 60-second, portrait creamy garlic Parmesan pasta video, controlled from an Android phone, using Google Colab for compute and a free-first workflow. Do not buy API credits, paid compute, subscriptions or upgrades.

## Repository

- User-maintained fork: https://github.com/markfox456-crypto/MoneyPrinterTurbo
- Default branch: `main`
- Current audited branch HEAD before this documentation update: `e43f7561ff032068b4b47ccbc8e497a829f05dae`
- This is a fork of the upstream project `harry0703/MoneyPrinterTurbo`; it contains application code and project-specific additions. Do not overwrite the fork wholesale with upstream.
- The Colab notebook now clones this maintained fork instead of the upstream repository, so the phone workflow uses the code tracked here.

## Confirmed project resources

- [Main English README](../README-en.md)
- [Android + Colab workflow guide](ANDROID_FREE_WORKFLOW.md)
- [Main Colab launch notebook](MoneyPrinterTurbo.ipynb)
- [No-paid-API cooking video assembler notebook](Free_Cooking_Video_Assembler_Colab.ipynb)
- [Editable local video project guide](video-projects.md)
- [Example configuration](../config.example.toml) — template only; do not place real keys in Git.
- [CI workflow](../.github/workflows/ci.yml)
- [Container security workflow](../.github/workflows/security.yml)
- [Docker publishing workflow](../.github/workflows/docker-ghcr.yml)

## User setup history (not a live runtime assertion)

1. Android/Termux: repository cloned to `~/MoneyPrinterTurbo`; Git 2.54.0 and Python 3.13.13 were available. The clone succeeded, but dependencies, launch and video rendering were not verified on Termux. Android is not one of the project's supported desktop platforms.
2. Switched to Google Colab so Android is the control device and the compute runs remotely.
3. Colab uses an isolated Python 3.11 environment, the repository lockfile, Streamlit WebUI and a temporary ngrok tunnel.
4. A previous ngrok token attempt failed with `ERR_NGROK_105`; a later session did reach a working WebUI tunnel. Tunnel URLs and tokens are temporary secrets and must not be written into this repository.
5. A prior WebUI generation attempt returned “API keys needed”. That message must be diagnosed by provider category: script/LLM, stock footage, and any other selected service may require separate credentials. A Pexels key is not a general-purpose LLM key.
6. The user's last reported UI settings were Pexels video source, portrait 9:16, maximum clip length 3 seconds, one video per run, Edge TTS voice `en-AU-Natasha-Female`, and music volume 20%. These settings are historical and have not been verified against a currently running Colab session.
7. A selected video provider later stopped issuing API responses temporarily. Stop repeated retries while it is unavailable; check provider status and quota before trying again.
8. The user later reported having two video clips for the cooking workflow. The actual files are not committed here or available for inspection in this repository snapshot. Their duration, content, source license and suitability remain unverified.

## Current code and notebook alignment

- `docs/MoneyPrinterTurbo.ipynb` was changed to clone `https://github.com/markfox456-crypto/MoneyPrinterTurbo.git`, not the upstream author's repository.
- It installs the fork in an isolated Python 3.11 environment using `uv sync --frozen`.
- It uses ngrok only to expose the remote Colab Streamlit UI; the notebook asks for the token interactively and does not save it to the notebook.
- The notebook's OpenRouter example requires a user's own API key even when selecting a free model. Free model availability, quotas and rate limits can change. This is not a keyless or unlimited generation guarantee.
- The separate [Free Cooking Video Assembler](Free_Cooking_Video_Assembler_Colab.ipynb) uses FFmpeg to assemble footage the user uploads. It does not call paid AI video-generation APIs. It cannot create missing cooking actions or certify the rights of uploaded material.

## Known issues / cautions

- “API keys needed” is a provider configuration issue. Identify the exact provider and whether it genuinely offers a free quota in the user's region before configuring it.
- Provider outage/rate-limit: do not repeatedly retry; wait or switch to footage already available.
- Colab free sessions can disconnect and reset. Save exported videos to the phone or Google Drive before the runtime ends.
- Never commit `config.toml`, API keys, ngrok tokens, passwords, cookies or temporary tunnel URLs.
- The Colab notebook should be re-run from top to bottom after a fresh runtime. The notebook's setup cell is designed to pull the latest `main` branch of this fork.
- The free assembler may repeat source clips to fill the 60-second timeline. Review the montage carefully; do not publish a repetitive or misleading edit.

## Next execution checklist

- [ ] Open the fork's Colab notebook on Android and run setup from a fresh runtime.
- [ ] Confirm the printed ngrok URL opens the WebUI; keep the URL private.
- [ ] Check the exact missing API provider message before adding any credential.
- [ ] If a genuinely free provider is unavailable, use the separate FFmpeg assembler with footage the user owns or is licensed to use.
- [ ] Inspect the two reported video files and confirm they depict the cooking actions represented in the voiceover.
- [ ] Assemble a coherent 60-second 9:16 cut; do not invent footage or silently repeat a small number of shots without review.
- [ ] Add a voiceover and music only when their use rights and source are acceptable.
- [ ] Export H.264 MP4 at 1080×1920 and watch the full video on the phone.
- [ ] Save the final export outside the temporary Colab runtime.

## What this update changed

Documentation and notebook alignment only. No application logic, provider credentials, user data, generated videos, or paid services were changed or added. The actual Colab runtime was not accessible through GitHub and has not been restarted or modified by this repository update.
