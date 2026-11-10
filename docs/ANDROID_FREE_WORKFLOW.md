# Android + Google Colab: Free-First MoneyPrinterTurbo Workflow

This guide is for controlling MoneyPrinterTurbo from an Android phone. It prioritizes free services and avoids paid subscriptions. It does **not** promise unlimited or permanently free AI generation: Google Colab free resources are variable, and MoneyPrinterTurbo's automated script/media providers may require API credentials.

## 1. What this setup can and cannot do

- Android is the control device; the heavy work runs in Google Colab's cloud runtime.
- Colab can run the repository notebook and expose the WebUI through a temporary tunnel.
- MoneyPrinterTurbo can automate parts of short-video production when its configured providers are available.
- A provider key is not the same as a subscription. However, free quotas, trials, and availability can change; check the provider's current terms before using it.
- If no usable free provider is available, do not enter payment details just to make the pipeline run. Use the manual footage workflow in section 6.

## 2. Open the project from your phone

1. Open the official project notebook: https://colab.research.google.com/github/markfox456-crypto/MoneyPrinterTurbo/blob/main/docs/MoneyPrinterTurbo.ipynb
2. Sign in to Google.
3. In Colab, choose **Runtime → Change runtime type**. Start with the default hardware; select a GPU only if Colab makes one available without payment.
4. Run notebook cells from top to bottom. Grant only the permissions the notebook requires.
5. Keep the Colab tab open while the runtime is working. Free runtimes can disconnect or stop when idle and have usage limits.

## 3. Start and open the WebUI

- Follow the notebook's launch cell and use the public/temporary URL it prints.
- Open that exact URL in a new browser tab on your phone.
- If the notebook displays `localhost`, `None`, or a blank link instead of a usable public URL, the tunnel did not start correctly. Re-run the tunnel/launch cell as instructed by the notebook; do not guess a URL.
- Treat tunnel URLs and access tokens as private. Do not post them publicly or commit them to GitHub.

## 4. Configure a cautious first test

Use a small test before attempting a full 60-second video:

| Setting | First-test value |
|---|---|
| Video orientation | Portrait 9:16 |
| Number of videos | 1 |
| Maximum clip length | 3–5 seconds |
| Topic | One simple cooking action |
| Language | English |
| Voice | A built-in/free voice only if currently available |
| Music | Off for the first test |

Provider setup depends on the current MoneyPrinterTurbo version and provider availability. Do not paste API keys into notebook output, screenshots, chat messages, or this repository. Store secrets only in the provider's intended secret/configuration mechanism, and never commit a populated `config.toml`.

## 5. If the app says “API keys needed”

This is a provider configuration issue, not a phone problem.

1. Identify which provider is missing a key: script/LLM, stock footage, or text-to-speech.
2. Check whether that provider currently offers a genuine free tier in your region.
3. If it does, use its official dashboard and observe quota/credit limits.
4. If it requires payment or a paid subscription, skip it.
5. Do not add random keys or use someone else's credentials. An expired or rate-limited key will not solve the problem.

A completely keyless, unlimited AI-video pipeline is not guaranteed by MoneyPrinterTurbo. If no free provider is currently usable, switch to section 6 rather than repeatedly retrying a failing generation task.

## 6. Guaranteed no-paid-API fallback: assemble footage you already have

For the first creamy garlic Parmesan pasta video, use your own clips or footage you have permission to use.

1. Collect the source clips in one folder in Google Drive.
2. Choose short sections showing: ingredients, chopping/mincing garlic, melting butter, adding garlic, adding cream, adding Parmesan, tossing pasta, and final plating.
3. Write a 60-second voiceover separately. Do not rely on generated visuals to show actions that did not happen.
4. Assemble in a free editor available to you, or use FFmpeg in a Colab notebook. Colab's free availability and session limits still apply.
5. Export 1080 × 1920 (9:16), H.264 MP4, with captions and music you are licensed to use.
6. Watch the complete export on your phone before publishing.

Suggested 60-second structure:

| Time | Visual |
|---|---|
| 0–4 s | Finished creamy pasta close-up |
| 4–10 s | Ingredients |
| 10–17 s | Boil pasta; reserve pasta water |
| 17–25 s | Butter and garlic in pan |
| 25–34 s | Add cream and Parmesan |
| 34–44 s | Add pasta and loosen with pasta water |
| 44–53 s | Toss, coat, and plate |
| 53–60 s | Parmesan, lemon/parsley garnish, final hero shot |

## 7. Troubleshooting

- **Colab disconnected:** reconnect and rerun the notebook cells in order. Temporary files may have been lost unless saved to Drive.
- **Tunnel URL is missing or invalid:** rerun the tunnel cell and open the newly printed URL.
- **“API keys needed”:** identify the exact provider and either configure a currently free key or use section 6.
- **Provider rate limit / temporarily unavailable:** stop retrying for a while; repeated requests may worsen the limit.
- **Video generation stops at the video stage:** inspect the final error lines in the Colab log. A successful FFmpeg check only confirms FFmpeg is available; it does not prove the upstream media provider succeeded.
- **Export has no sound:** verify the selected voice/music tracks and final audio-mix settings.

## 8. Safety and cost checklist

- [ ] Google Colab is using a free runtime, not a paid compute unit.
- [ ] No provider requiring payment is selected.
- [ ] No API key, tunnel token, password, or private URL is committed to GitHub.
- [ ] Source clips, music, and images are licensed for the intended use.
- [ ] The final video is watched on the phone before publishing.

## Official project references

- Repository: https://github.com/markfox456-crypto/MoneyPrinterTurbo
- Colab notebook: https://colab.research.google.com/github/markfox456-crypto/MoneyPrinterTurbo/blob/main/docs/MoneyPrinterTurbo.ipynb
- English README: https://github.com/markfox456-crypto/MoneyPrinterTurbo/blob/main/README-en.md

---
This is a user workflow guide, not a modification of MoneyPrinterTurbo's application code. Provider pricing, quotas, and Colab availability can change; verify them at the time of use.
