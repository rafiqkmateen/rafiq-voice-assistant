# Meet Khadijah

**A personal AI voice assistant with a live dashboard and a face, built and run on one Windows PC.**
Designed and built by **Rafiq Mateen**, AI creator.

![Khadijah talking, mid-reply: TALKING under the glass planet, the rings lit](images/khadijah-talking.png)

**[Watch a short demo, with her real voice and her face](video/khadijah-demo.mp4)**

You talk to her, or type to her. She thinks with Claude, answers out loud in her own voice, which is cloned on the PC itself from a short recording, and runs a live dashboard around her: calendar and tasks, brokerage reports, local news and weather, sports, cinema listings, the machine's own health, the devices on the Wi-Fi, WhatsApp, and DaVinci Resolve video builds. Everything runs locally; nothing listens on the network.

---

## What she can do

| Area | Highlights |
|---|---|
| **Voice** | Hands-free conversation; replies spoken in a voice cloned on-device with F5-TTS (ElevenLabs as the switch-back); never hears herself; Escape stops her mid-sentence; say "open Calendar" or "go to Tasks" and the screen goes there; click a menu section and she says one short line about it (a Narrate switch turns that off) |
| **Brains** | Claude Haiku by default, Sonnet or Gemini by voice; hard questions move to Sonnet on their own (model routing), with an hourly cap; falls back gracefully when a model fails |
| **The dashboard** | A window of sections: a menu down the left, a stage in the middle, a panel on the right with her face (a short video that plays while she talks and fades softly into the screen: a see-through cut-out with a soft edge, no frame, with her name, state and model under it) and a dock along the bottom. Home has a looping night video of the city behind the rings. Home shows glowing rings, one per group, with each group's node logos riding its ring; every node opens its own card on the stage; a Claude plan-limit card shows usage and spend, and its node wears a red halo, and the menu shows the percentage blinking in red, when the session or the week is at 90 percent; the top bar of a wide window shows the date and time at its right end; the control bar has a RESTART button next to STOP KHADIJAH, which stops her exactly as STOP does and then starts her again a few seconds later |
| **Calendar and tasks** | Your Google Calendar month on screen: click a day to add an event, click an event to change or delete it, and it is saved straight to Google. Tasks are ticked, added, edited and deleted by mouse or by voice ("add task buy milk", "undo that"). Ask her about your schedule for any dates up to a year ahead ("what is my schedule for next month?") and she reads the calendar live and summarizes it, read-only. Times and dates follow the PC's own clock and date style (24-hour or 12-hour; day, month or year first) |
| **Money, read-only** | Interactive Brokers and Webull balances and positions as reports, graded from strong to critical; one click asks a Claude project to pull the live positions, read the news on the movers and write a thesis and a pro's read for each, with the broker access and limits that project's own instructions set. Khadijah's own code never places a trade, and an automated check enforces it |
| **Local life** | Weather in °F, currency outlook and local alerts; the Cartagena news card draws the dollar's recent trend as a line chart, oldest rate at the left, newest at the right, with the span of days beside it; films showing nearby with posters and English synopses; five pro teams' scores and standings |
| **WhatsApp** | Every chat on one screen with its own reply box; voice notes are written out as text on the PC, messages show in English and replies go out in the contact's language; a morning brief arrives on the phone at 7 AM |
| **The machine** | Live CPU, memory, GPU and disk readout; a disk auditor with a preview-first junk cleaner; a Wi-Fi map that flags unknown devices and links to the router to check them; a weekly security check for Node.js and Python packages, which she also runs when asked |
| **Creative tools** | Plans drone missions on a map, imports the footage with a confirm step and sorts it by mission; builds one DaVinci Resolve timeline per clip, named after the clip, with the DJI D-Log M to Rec.709 color file on each, and renders one finished video per clip; DaVinci Resolve Studio opens by itself when its node is clicked |
| **Market research** | Tears down any website in a hidden Chrome tab: its tech stack, a rebuild recipe, and what the evidence can't show; a local LLM for day-to-day questions at no ongoing SaaS cost; a "Great Debate" where two AI voices argue a plan until they agree |
| **Web and screen** | Web search with a spoken summary (Tavily, falling back to DuckDuckGo); a tabbed Google News card (Home, For you, Following and a row of sections), each headline a link to its article; looks at a screen and describes it, after asking which screen she may look at (the laptop screen, another monitor, or all of them) |

## A look around

Home is the first screen: the menu of sections down the left, the groups' nodes riding glowing rings across a looping night video of the city, her globe in the panel on the right, the machine readout along the top and the typing box along the bottom. The rings light up in waves while she listens, thinks or talks. The demo video shows her face look; the pictures below show the glass-planet look of her globe.

**Standing by.** The menu on the left, the rings of nodes over the night video, the glass planet on the right with STANDBY and MIC OFF under it, and the machine readout at the top.

![Khadijah standing by: the rings of nodes, and the glass planet in the right-hand panel](images/khadijah-standby.png)

**Listening.** The word under the glass planet changes to LISTENING while she hears you, and the button at the bottom reads "Mic on".

![Khadijah listening: LISTENING under the glass planet in the right-hand panel](images/khadijah-listening.png)

**The calendar.** A month of Google Calendar, today outlined, with arrows and a Today button. (The events shown are made up.)

![The Calendar section, October 2026, with the glass planet in the right-hand panel](images/khadijah-calendar.png)

**Adding an event.** Click a day and the form opens beside the month; Save puts it on Google Calendar.

![The New event form beside the month](images/khadijah-calendar-new-event.png)

**Tasks.** Open tasks and coming calendar items in one list, with an Add box at the bottom. (The tasks shown are made up.)

![The Tasks section: open tasks and calendar items, with the Add box at the bottom](images/khadijah-tasks.png)

**Google News.** A tabbed card (Home, For you, Following and a row of sections); each headline is a link to its article.

![The Google News card open beside the Google group's list](images/khadijah-google-news.png)

**Every part of the screen, labeled in plain words** (the glass planet is in the right-hand panel).

![What is on the screen, labeled: the menu, the nodes, the machine readout, the glass planet, the message box and the stop and mic buttons](images/whats-on-the-screen.png)

## How it is built

![The five programs and how they talk](images/how-it-is-built.png)

| Part | Built with |
|---|---|
| Server | Python 3.12, FastAPI, WebSocket; split into routes, services and model clients |
| Dashboard | Plain JavaScript with no build step, a glass-panel design system, three.js only for the glass-planet look of her globe (her face is a short video that fades softly into the screen, a see-through cut-out with a soft edge) |
| Models | Anthropic API (Claude Haiku and Sonnet), Google Gemini, with routing, fallbacks and rate limits |
| Voice | F5-TTS running on the graphics card in its own Python environment; ElevenLabs as the alternative |
| WhatsApp | A Node.js bridge on Baileys, supervised and restarted by the server |
| Data | Broker interfaces (read-only), Google Calendar (through a service account that may only touch events), Google News feeds, ESPN, weather and currency feeds, cinema sites and any site Reverse Engineer tears down, read through a hidden Chrome |

**Engineering choices worth a look**

- **Local-only by design.** Every service binds to 127.0.0.1; the server checks Host and Origin on every request and on the WebSocket, and sends a strict Content Security Policy.
- **Read-only money, enforced by code.** Broker access is limited to account reads, and a checker scans the code for any order-placing call.
- **A tripwire on its own files.** A watchdog keeps a cryptographic fingerprint of the project's real working files — leaving out the ones that are generated, downloaded or copied by design — and re-checks them every twenty seconds, logging each change. If a file's content ever goes back to something it held earlier — the signature of a silent revert — it raises an alert on the desktop with a beep. It also reports anything that changed while it was not running.
- **Documentation tested against the code.** A script checks the guide against the real files, names and load order, so the docs cannot drift.
- **Built with AI, engineered like software.** Developed with Claude Code under written working rules: backups before every change, byte-verified writes, one commit per session.

## The code

The source code is private. If you would like to review it, contact me and I will give you access.

## Credits

Khadijah began from Julian Ivanov's open-source jarvis-voice-assistant template and was rebuilt from there into what you see here.

© 2026 Rafiq Mateen. All rights reserved.

<!-- 4a-fingerprint: 658fa3de4c9113b7 -->
