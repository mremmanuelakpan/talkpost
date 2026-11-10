# Voice-to-Video Studio (prototype v3)

A single-file, browser-only prototype that turns a voice recording into a shareable video. No backend, no accounts: audio is processed locally in the browser.

The purpose of this prototype is to answer one question: **can a phone reliably export a postable video from a browser?**

## Run it

Open `index.html`, or host the folder on any static host (GitHub Pages, Netlify, Cloudflare Pages).

Recording from the microphone needs **HTTPS**. Uploading an audio file works anywhere.

To use GitHub Pages: repo Settings > Pages > Deploy from branch > `main` / root.

## What it does

- One-screen mobile layout: the preview stays on top, and five swipeable cards (Audio, Visual, Backdrop, Text, Format) sit below it with Generate pinned at the bottom
- Record or upload audio
- Two visual styles: waveform line and equaliser bars
- Backgrounds: gradient, solid colour, or your own image
- Sizes: 9:16, 1:1, 4:5 at 720p or 1080p
- Title, subtitle, font and text size, optional glow
- Boosts quiet audio toward a speech-friendly level
- Exports MP4 (H.264/AAC) when the browser supports it, otherwise WebM
- Diagnostics report (tap Report, then Copy report) you can paste after each export

## Known limits

- Export runs in **real time**: a 60-second clip takes about 60 seconds, and the screen must stay on with this tab in the foreground.
- Output format depends on the browser. Chrome on Android produced H.264 MP4. Desktop Chrome may produce VP9/Opus, which the app labels honestly and warns about.
- System fonts only (canvas can only draw fonts that are already loaded).
- Platforms may recompress uploads or change their rules; the size options are conveniences, not guarantees.

## Test checklist

Copy the diagnostics report after each run.

1. 60-second clip, 9:16, 720p, equaliser, glow off
2. Same clip with glow on, then at 1080p
3. Image background in 4:5
4. iPhone Safari
5. Post an exported file to WhatsApp status and Instagram

## Go / pivot / kill

- **Continue:** a 60-second clip exports in roughly real time on a mid-range Android and an iPhone, and posts without conversion.
- **Pivot:** only WebM works, so server-side conversion would be needed.
- **Kill:** exports fail often on mid-range Android.
