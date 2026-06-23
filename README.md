# 🎬 Screen Recorder → MP4

> A browser-based screen recorder that captures your screen with audio and saves **straight to MP4** — no installs, no dependencies, no server. The entire app is a single `index.html` written in plain JavaScript.

[![License: MIT](https://img.shields.io/badge/License-MIT-e8557f.svg)](LICENSE)
[![Live Demo](https://img.shields.io/badge/Live-Demo-4a90e2.svg)](https://<your-username>.github.io/<repo-name>/)

<img width="585" height="846" alt="Screenshot 2026-06-23 at 7 41 20 PM" src="https://github.com/user-attachments/assets/c850f93f-413a-4664-b2a8-d908ad31eaf8" />


---

## Overview

Most screen recorders mean an install, an account, or a watermark. This one runs entirely in the browser: open the page, pick what to capture, and record. It writes the video **directly to disk as an MP4 while recording**, so a take can run as long as your free disk space allows — and it actively protects you from ending up with a broken or empty file.

## ✨ Features

- **Screen + audio** — system audio and/or microphone, mixed into a single track.
- **Saves to MP4** (H.264 / AAC) natively where supported; otherwise records WebM and converts to MP4 in-browser.
- **Unlimited length** — streams to disk *while* recording, limited only by free disk space.
- **Quality presets** — 720p / 1080p / native, each with a matching bitrate.
- **Live HUD** — capture resolution, recorded size, free space, and time-left, updated every second (with an optional floating pop-out window).
- **Safeguards** — auto-stops before the disk fills, detects a frozen capture and auto-pauses, and warns if a recording ends up empty, so you never lose a take.
- **Pause / resume**, live timer, and a clean cream-and-pink UI.

## 🛠 How it works

| Concern | Web API |
|---|---|
| Screen + system audio | `getDisplayMedia` |
| Microphone | `getUserMedia` |
| Mixing audio sources | Web Audio API (`AudioContext` → `MediaStreamDestination`) |
| Encoding | `MediaRecorder` |
| Unlimited streaming to disk | File System Access API (`showSaveFilePicker` + `createWritable`) |
| Free-space readout | `navigator.storage.estimate()` |
| Freeze detection | `requestVideoFrameCallback` + track `mute` / `unmute` |
| Floating counter | Document Picture-in-Picture API |
| WebM → MP4 fallback | `@ffmpeg/ffmpeg` (WebAssembly) |

No frameworks — vanilla JavaScript in one HTML file.

## ✅ Browser support

Best in **Chrome** and **Edge** (native MP4 recording, streaming to disk, floating counter). **Firefox** and **Safari** work via the WebM → MP4 fallback.

## ⚠️ Note on macOS

Browsers can't capture system audio on macOS (an OS-level restriction), so on a Mac the app records **screen + microphone**. To record fullscreen video with its sound on macOS, a native recorder plus a virtual audio device (e.g. BlackHole) is the reliable route.

## 📄 License

[MIT](LICENSE) © 2026 Hloriia Ziubrovska
