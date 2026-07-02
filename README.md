# Image·Video Cloud GUI

A single-file web GUI for generating **images and video** through the [OpenRouter](https://openrouter.ai) unified API. No build step, no dependencies, no server — just open `index.html` in Chrome or Edge.

![status](https://img.shields.io/badge/dependencies-zero-brightgreen) ![license](https://img.shields.io/badge/license-MIT-blue)

## Features

- 🔑 **Bring your own key** — paste your OpenRouter API key in the app. It's stored only in your browser's localStorage and sent only to `openrouter.ai`. Nothing is hardcoded; a "Forget" button wipes it.
- 📋 **Live model dropdowns** — image and video model lists are fetched from OpenRouter's catalog endpoints (`/api/v1/images/models`, `/api/v1/videos/models`) at load, grouped by provider, with an offline snapshot fallback. Every image/video model on OpenRouter shows up automatically.
- 🎛 **Capability-aware controls** — resolution and aspect-ratio dropdowns adapt to what the selected model actually supports.
- 🖼 **Image generation** — `POST /api/v1/images`, up to 10 images per call, png/jpeg/webp, SVG-aware for vector models (Recraft).
- 🎬 **Video generation** — async `POST /api/v1/videos` → status polling → automatic mp4 download. Duration, resolution, aspect ratio, and audio toggles.
- 📁 **Output folder picker** — File System Access API (Chrome/Edge); every generation auto-saves as `YYYY-MM-DDTHHMMSS-<prompt-slug>.<ext>`. Falls back to browser Downloads.
- 🕘 **Generation history** — prompt, model, cost, and filename for the last 200 generations (localStorage), with prompt-reuse and JSON export.

## Usage

1. Get an API key at [openrouter.ai → Settings → API Keys](https://openrouter.ai/settings/keys) and load some credits.
2. Open `index.html` in Chrome or Edge (folder-saving needs the File System Access API; other browsers fall back to Downloads).
3. Paste the key → **Save key**.
4. Optionally **Choose folder…** for where outputs land.
5. Pick a model, write a prompt, generate.

Videos are asynchronous — expect 1–5 minutes depending on model and resolution. The app polls every 10 seconds and saves the mp4 automatically when done.

## Privacy

Your API key and generation history never leave your machine except for requests to `openrouter.ai`. There is no backend, no analytics, no telemetry.

## License

MIT
