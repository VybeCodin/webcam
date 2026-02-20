<p align="center">
  <img src="banner.png" alt="Sofa Engineer — vibe coding from the couch" width="100%">
</p>

# VybeCoding Webcam Companion

**Stream your desktop webcam to [VybeCoding](https://vybecoding-rho.vercel.app) on your iPhone.** The companion app that makes vibe coding with a live camera feed possible.

---

## What is this?

VybeCoding Webcam is a lightweight desktop companion app that streams your computer's webcam to the VybeCoding iOS app over your local Wi-Fi network. It's designed for developers who vibe code from their phone and want to see a live camera feed — whether that's monitoring a 3D printer, keeping an eye on a server rack, pair programming with a physical whiteboard, or just having a face cam while you code remotely.

## What is Vibe Coding?

Vibe coding is a new way of building software — coding by feel, using natural language and AI to write, run, and deploy code. Instead of memorising syntax, you speak your intent and let AI translate it into real commands. VybeCoding is the vibe coding terminal for iPhone: an AI-powered SSH client that turns plain English into shell commands, with voice control, safety analysis, and a full terminal experience on your phone.

## Why do I need the Webcam Companion?

iPhones can't directly access your Mac or PC's webcam over the network. This companion app bridges that gap:

- **Streams your webcam** as an MJPEG feed over your local network
- **Auto-discovered** by VybeCoding on your iPhone via Bonjour/mDNS — no IP addresses to type
- **Secure by default** — authenticated with a per-session token, never leaves your local network
- **Runs in the background** from your system tray — start it once and forget about it
- **Zero config** — just click Start and open VybeCoding on your phone

## Features

- Live MJPEG webcam streaming over Wi-Fi
- Automatic device discovery (Bonjour/mDNS) — your iPhone finds your computer instantly
- Per-session authentication token — no one else on your network can access the stream
- Camera and microphone selection
- Adjustable resolution (480p, 720p, 1080p) and frame rate (15/24/30 fps)
- Live preview in the companion app window
- System tray mode — runs silently in the background
- macOS signed and notarized — installs without Gatekeeper warnings
- Built with Electron and Express for a native desktop experience

## Download

Head to the [**Releases**](https://github.com/VybeCodin/webcam/releases) page and download the latest version:

| Platform | Format |
|----------|--------|
| macOS    | `.dmg` (signed + notarized) |
| Windows  | Coming soon |
| Linux    | Coming soon |

## Quick Start

1. **Download and install** the app from [Releases](https://github.com/VybeCodin/webcam/releases)
2. **Open VybeCoding Webcam** on your Mac
3. **Select your camera** and click **Start Streaming**
4. **Open VybeCoding** on your iPhone and tap the **Webcam** button on any server
5. Your live camera feed appears instantly — no setup needed

## How It Works

```
Your Mac                          Your iPhone
┌──────────────────────┐          ┌──────────────────────┐
│  VybeCoding Webcam   │          │     VybeCoding       │
│  Companion App       │◄────────►│     iOS App          │
│                      │  Wi-Fi   │                      │
│  Webcam → MJPEG      │  (LAN)   │  Webcam tab shows    │
│  stream on port 3002 │          │  live camera feed    │
└──────────────────────┘          └──────────────────────┘
```

1. The companion app captures your webcam using ffmpeg and serves it as an MJPEG stream
2. It advertises itself on your local network via Bonjour (`_termy-cam._tcp`)
3. VybeCoding on your iPhone discovers the service automatically
4. The app authenticates using a per-session token published in the Bonjour TXT record
5. Your live webcam feed appears in the VybeCoding app — pinch to zoom, tap to snapshot

## Privacy & Security

- **Local only** — your webcam stream never leaves your Wi-Fi network
- **Per-session tokens** — a new authentication token is generated every time the app starts
- **No cloud** — no data is sent to any server, ever
- **No accounts** — no sign-up, no tracking, no analytics
- **Open source** — you can see exactly what the app does

## Use Cases for Vibe Coding

- **Monitor your dev environment** — keep an eye on hardware, LEDs, or a 3D printer while coding from your phone
- **Pair programming** — point your webcam at a whiteboard and reference it from your terminal
- **Remote server rooms** — check on physical hardware while SSH'd in from your couch
- **Live coding streams** — use your desktop webcam as a face cam while vibe coding on your phone
- **Home lab monitoring** — watch your Raspberry Pi cluster while deploying from VybeCoding

## Tech Stack

- **Electron** — native desktop app with system tray support
- **Express** — lightweight HTTP server for the MJPEG stream and configuration API
- **ffmpeg** — hardware-accelerated webcam capture (bundled, no install needed)
- **Bonjour/mDNS** — zero-config network discovery via `bonjour-service`

## Requirements

- macOS 10.15+ (Catalina or later)
- A webcam connected to your computer
- VybeCoding app on your iPhone (same Wi-Fi network)

## Building from Source

```bash
git clone https://github.com/VybeCodin/webcam.git
cd webcam
npm install
npm start        # Run in development mode
npm run build    # Build for distribution
```

## About VybeCoding

VybeCoding is the vibe coding terminal for iPhone. It's an AI-powered SSH client that lets you:

- **Speak commands** — say "list all files" and it runs `ls -la`
- **AI safety analysis** — every command is checked before execution
- **VNC remote desktop** — see and control your server's GUI
- **SFTP file transfer** — browse and manage files visually
- **Multi-tab sessions** — connect to multiple servers at once
- **Webcam streaming** — see your desktop camera feed (that's what this companion app is for!)

Learn more at [vybecoding-rho.vercel.app](https://vybecoding-rho.vercel.app)

---

Built by [SOBYTES LTD](https://sobytes.com) for the vibe coding community.
