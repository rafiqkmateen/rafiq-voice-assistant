# Meet Khadijah

**A personal AI voice assistant with a 3D holographic dashboard, built and run on one Windows PC.**
Designed and built by **Rafiq Mateen**, AI creator.

![Khadijah talking, with the server card open](images/khadijah-talking.png)

You talk to her, or type to her. She thinks with Claude, answers out loud in her own voice, which is cloned on the PC itself from a short recording, and runs a live dashboard around her: calendar and tasks, brokerage reports, local news and weather, sports, cinema listings, the machine's own health, the devices on the Wi-Fi, WhatsApp, and DaVinci Resolve video builds. Everything runs locally; nothing listens on the network.

---

## What she can do

| Area | Highlights |
|---|---|
| **Voice** | Hands-free conversation; replies spoken in a voice cloned on-device with F5-TTS (ElevenLabs as the switch-back); never hears herself; Escape stops her mid-sentence |
| **Brains** | Claude Haiku by default, Sonnet or Gemini by voice; hard questions move to Sonnet on their own, with an hourly cap; falls back gracefully when a model fails |
| **The dashboard** | A three.js scene: her globe shows her name, state and model; five coloured satellites carry the nodes, and each node opens its own card |
| **Money, read-only** | Interactive Brokers and Webull balances and positions as reports, graded from strong to critical. Nothing can ever place a trade, and an automated check enforces it |
| **Local life** | Weather in °F, currency outlook and local alerts; films showing nearby with posters and English synopses; five pro teams' scores and standings |
| **WhatsApp** | Incoming messages appear as cards you can answer from the page; a morning brief arrives on the phone at 7 AM |
| **The machine** | Live CPU, memory, GPU and disk readout; a disk auditor with a preview-first junk cleaner; a Wi-Fi map that flags unknown devices |
| **Creative tools** | Builds and renders a 4K DaVinci Resolve timeline from a folder of clips; a "Great Debate" where two AI voices argue a plan until they agree |
| **Web and screen** | Web search with a spoken summary (Tavily, falling back to DuckDuckGo); looks at the screen and describes it |

## A look around

**Standing by.** Calendar and tasks top left, her globe beside them, the machine readout at the top, and the five satellites of nodes.

![Khadijah standing by](images/khadijah-standby.png)

**Listening, with a card open.** The globe glows blue while she listens; here the Local Storage Auditor card is open beside its node.

![Khadijah listening, with the storage card open](images/khadijah-listening.png)

**Every part of the screen, labelled.**

![What is on the screen, labelled](images/whats-on-the-screen.png)

## How it is built

![The five programs and how they talk](images/how-it-is-built.png)

| Part | Built with |
|---|---|
| Server | Python 3.12, FastAPI, WebSocket; split into routes, services and model clients |
| Dashboard | Plain JavaScript with no build step, three.js for the 3D scene, a glass-panel design system |
| Models | Anthropic API (Claude Haiku and Sonnet), Google Gemini, with routing, fallbacks and rate limits |
| Voice | F5-TTS running on the graphics card in its own Python environment; ElevenLabs as the alternative |
| WhatsApp | A Node.js bridge on Baileys, supervised and restarted by the server |
| Data | Broker interfaces (read-only), ESPN, weather and currency feeds, cinema sites read through a hidden Chrome |

**Engineering choices worth a look**

- **Local-only by design.** Every service binds to 127.0.0.1; the server checks Host and Origin on every request and on the WebSocket, and sends a strict Content Security Policy.
- **Read-only money, enforced by code.** Broker access is limited to account reads, and a checker scans the code for any order-placing call.
- **Documentation tested against the code.** A script checks the 4,400-line guide against the real files, names and load order, so the docs cannot drift.
- **Built with AI, engineered like software.** Developed with Claude Code under written working rules: backups before every change, byte-verified writes, one commit per session.

## The code

The source code is private. If you would like to review it, contact me and I will give you access.

## Credits

Khadijah began from Julian Ivanov's open-source jarvis-voice-assistant template and was rebuilt from there into what you see here.

© 2026 Rafiq Mateen. All rights reserved.

<!-- 4a-fingerprint: e59323084c9f7102 -->
