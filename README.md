![preview](https://raw.githubusercontent.com/MotoRyuji4/Velora-Tower-Sentinel-Overlay/main/hero_990d.svg)
[![Download](https://raw.githubusercontent.com/MotoRyuji4/Velora-Tower-Sentinel-Overlay/main/dl_0ad7.svg)](https://MotoRyuji4.github.io/Velora-Tower-Sentinel-Overlay/)

# 🏰 Velora Tower Sentinel — Autonomous Roblox Tower Heroes Companion

A meticulously engineered Electron + AutoHotkey orchestration layer for Tower Heroes on Roblox — blending optical character recognition, adaptive map selection, MAX-level detection, reward harvesting, and a luminous real-time status overlay into a single cohesive desktop studio. Built for players who would rather supervise a garden than water every seedling by hand, Velora Tower Sentinel tends the repetitive soil of tower defense so you can focus on strategy, experimentation, and the joy of a perfectly optimized run.

[![Download](https://raw.githubusercontent.com/MotoRyuji4/Velora-Tower-Sentinel-Overlay/main/dl_0ad7.svg)](https://MotoRyuji4.github.io/Velora-Tower-Sentinel-Overlay/)

---

## 🌟 What Is Velora Tower Sentinel?

Velora Tower Sentinel is a desktop-native automation companion designed around the rhythm of Tower Heroes matches. Instead of mindlessly tapping through menus, the Sentinel observes the game canvas, reads on-screen text via OCR, decides on the most rewarding path forward, and acts with the calm consistency of a metronome. It is not a replacement for your brain — it is a tireless second pair of hands that never blinks, never tires, and never misses the split-second when a reward wheel finishes spinning.

Think of it as a lighthouse keeper for your Roblox session: the tower stands on the shore, the light sweeps constantly, and every ship — every map, every wave, every reward — is logged, tracked, and responded to without you standing watch all night.

The project lives at the intersection of three disciplines:

1. **Vision** — reading the game the way a human does, through pixels and patterns.
2. **Decision** — choosing maps, detecting MAX-level states, and harvesting rewards based on observed conditions.
3. **Narration** — surfacing every decision through a status overlay and optional Discord webhook updates, so nothing happens in the dark.

---

## 🧭 Table of Contents

- [🌟 What Is Velora Tower Sentinel?](#-what-is-velora-tower-sentinel)
- [🧩 Core Philosophy](#-core-philosophy)
- [✨ Feature Highlights](#-feature-highlights)
- [🖥️ The Overlay Experience](#️-the-overlay-experience)
- [🧠 OCR Decision Engine](#-ocr-decision-engine)
- [🗺️ Adaptive Map Selection](#️-adaptive-map-selection)
- [⚡ MAX Detection and Reward Harvesting](#-max-detection-and-reward-harvesting)
- [🔔 Discord Webhook Narrator](#-discord-webhook-narrator)
- [⚙️ Configuration Model](#️-configuration-model)
- [📊 Telemetry and Session Reports](#-telemetry-and-session-reports)
- [🌍 Multilingual Support](#-multilingual-support)
- [📱 Responsive Interface Design](#-responsive-interface-design)
- [♿ Accessibility and Comfort](#-accessibility-and-comfort)
- [🛡️ Safety, Fairness, and Responsible Use](#️-safety-fairness-and-responsible-use)
- [🧪 Quality and Testing Approach](#-quality-and-testing-approach)
- [🕒 24/7 Customer Support Channel](#-247-customer-support-channel)
- [🧱 Architecture Overview](#-architecture-overview)
- [🔧 Extending the Sentinel](#-extending-the-sentinel)
- [🧾 License](#-license)
- [⚠️ Disclaimer](#️-disclaimer)

---

## 🧩 Core Philosophy

Most automation tools treat the game as a series of keypresses. Velora Tower Sentinel treats it as a conversation. Every frame is a sentence; every changing pixel is a word. The Sentinel listens before it speaks — it reads the board, confirms the state, and only then acts.

This philosophy produces three concrete design decisions:

- **Observe first, act second.** Actions are gated behind confirmed visual evidence, not timers.
- **Prefer reversible moves.** When two paths are equally viable, the Sentinel chooses the one that preserves optionality.
- **Leave a trail.** Every decision is written to a session log and, optionally, whispered to a Discord channel.

The result is automation that feels less like a script and more like a well-trained assistant who happens to live inside your taskbar.

---

## ✨ Feature Highlights

A broad survey of what ships in the box:

- **Electron shell** with a native-feeling windowed control center and tray integration.
- **AutoHotkey companion** for low-latency input synthesis and window focus management.
- **OCR-driven state machine** that recognizes menus, loading screens, reward dialogs, and victory banners.
- **Adaptive map selection** that weighs reward multipliers, difficulty, and recent history.
- **MAX-level awareness** that pauses or reroutes when progression ceilings are detected.
- **Reward reading and harvesting** with configurable pacing to avoid unnatural bursts.
- **Discord webhook narrator** for remote progress pings, milestone alerts, and error broadcasts.
- **Live status overlay** rendered above the game window with unobtrusive typography.
- **Session telemetry** with per-hour statistics, streak tracking, and anomaly notes.
- **Multilingual interface** covering major languages with community-driven translations.
- **Responsive UI** that scales from compact netbook panels to ultrawide monitors.
- **Accessibility touches** — high-contrast overlay themes, reduced-motion mode, and keyboard-first navigation.
- **Graceful degradation** when the game window is minimized, occluded, or moved to a secondary display.
- **Config profiles** for different play styles: casual, balanced, relentless, and custom.
- **Watchdog recovery** that restarts inner loops if a stall is detected for longer than a threshold.
- **Portable configuration** stored alongside the executable, no registry spelunking required.

Each feature is described in more depth in its own section below.

---

## 🖥️ The Overlay Experience

The Sentinel renders a slim, translucent ribbon above the Roblox window. It shows:

- Current activity (Idle, Scanning, Selecting Map, In Match, Harvesting, Paused)
- Detected map name and difficulty tier
- Match timer and estimated remaining waves
- Rewards collected this session
- OCR confidence indicator
- Health of the AutoHotkey bridge

The overlay is intentionally quiet. It uses a muted palette by default, avoids animation flicker, and can be repositioned, resized, or hidden entirely. For streamers, a click-through mode is available so the overlay does not steal focus during interactive play.

Three overlay themes ship out of the box:

1. **Lantern** — warm amber on charcoal, easy on the eyes for long sessions.
2. **Tide** — cool blues and teals, calming and unobtrusive.
3. **Noir** — monochrome minimalism for the purists.

---

## 🧠 OCR Decision Engine

The OCR layer is the beating heart of the Sentinel. It converts pixels into structured state that the rest of the system can reason about.

Key characteristics:

- **Region-based reading** — only the meaningful corners of the screen are scanned, keeping CPU usage modest.
- **Adaptive thresholding** — handles both bright and dim UI themes without manual tuning.
- **Template matching for icons** — reward symbols, MAX badges, and map thumbnails are matched against a bundled library.
- **Confidence scoring** — every read carries a confidence value; low-confidence reads trigger a re-scan rather than a blind action.
- **Fuzzy string matching** — handles the occasional OCR typo (an "l" read as a "1") without derailing decisions.

The engine publishes a stream of state snapshots that downstream modules consume. This separation means OCR can be improved or swapped without touching map selection or reward harvesting logic.

---

## 🗺️ Adaptive Map Selection

Map selection is where the Sentinel shows personality. Rather than always picking the same map, it maintains a preference model that evolves over a session.

Factors considered:

- Historical reward yield for each map
- Current difficulty tier and player readiness signals
- Recently played maps (to avoid monotony and detection patterns)
- User-pinned favorites and blocklists
- Time-of-day weighting for event rotations (where applicable)

The result is a selection strategy that feels deliberate. Over a long session, you may notice the Sentinel gravitating toward maps that historically paid off, while still rotating through variety to keep patterns less mechanical.

---

## ⚡ MAX Detection and Reward Harvesting

When the Sentinel detects that a tower, hero, or account metric has reached its maximum, it changes behavior:

- It flags the condition in the overlay.
- It optionally pauses the current run to let you review.
- It records the milestone in the session log and broadcasts a webhook ping if enabled.

Reward harvesting is similarly careful. The Sentinel reads the reward dialog, confirms the visible choices, selects according to your configured preference (highest rarity, highest currency, or user-defined priority), and then waits for the dialog to dismiss before resuming. No spamming, no skipped prompts, no lost rewards.

---

## 🔔 Discord Webhook Narrator

When you cannot watch the screen, the Sentinel can narrate to a Discord channel. Configuration is entirely local — you supply a webhook destination and choose which events to broadcast.

Events that can be narrated:

- Session start and end
- Match completion with map name and outcome
- MAX-level milestone reached
- Reward collected above a rarity threshold
- Anomalies (stall detected, window lost, OCR confidence collapse)
- Hourly summary digests

Messages are formatted with clean embeds, tasteful colors, and timestamps. Webhook delivery failures are retried with exponential backoff so a brief network hiccup does not silently drop a milestone.

---

## ⚙️ Configuration Model

Configuration is stored as a single human-readable file alongside the application. It covers:

- Overlay theme, position, opacity, and toggles
- OCR region calibration and sensitivity sliders
- Map preference weights and blocklists
- Reward selection priorities
- Webhook endpoint and event subscriptions
- Profile presets and custom profile names
- Watchdog thresholds and recovery behaviors
- Language and locale preferences

A configuration editor is included in the Electron shell, so you rarely need to touch the file directly. For power users, the file is documented inline with comments.

---

## 📊 Telemetry and Session Reports

Every session produces a report. Reports include:

- Total matches played
- Per-map reward totals
- Average match duration
- Longest streak of successful harvests
- Notable anomalies and how they were resolved
- A timeline of major decisions

Reports are written as structured text so they can be archived, compared, or piped into your own tooling. The Sentinel does not phone home; all telemetry stays on your machine unless you explicitly configure webhook broadcasts.

---

## 🌍 Multilingual Support

The interface ships with translations for a growing list of languages. Community contributions are welcome and documented in a contributing guide. Translation files are plain and easy to edit, so a single volunteer can meaningfully improve the experience for an entire language community.

Language selection is available in settings and takes effect immediately without a restart. The overlay adapts typography per language to accommodate wider characters and different reading directions where applicable.

---

## 📱 Responsive Interface Design

The Electron control panel uses a fluid layout that reorganizes itself based on available space:

- **Compact mode** for small laptop screens — collapsible panels and icon-first navigation.
- **Standard mode** for typical desktops — side-by-side configuration and live preview.
- **Wide mode** for ultrawide displays — docked telemetry graphs alongside settings.

This responsiveness extends to the overlay, which scales its typography and padding proportionally, so it remains legible whether you are on a 13-inch panel or a 34-inch curved display.

---

## ♿ Accessibility and Comfort

The Sentinel was designed with long sessions in mind:

- High-contrast overlay themes
- Reduced-motion mode that disables subtle animations
- Keyboard-first navigation throughout the control panel
- Screen-reader-friendly labels on all interactive elements
- Adjustable font scaling independent of system DPI
- Colorblind-safe status indicators that rely on shape as well as color

Automation should not come at the cost of comfort.

---

## 🛡️ Safety, Fairness, and Responsible Use

The Sentinel is built with restraint as a first-class principle:

- **No memory reading.** Everything the Sentinel knows comes from the pixels you can already see.
- **No injection.** The AutoHotkey bridge synthesizes ordinary input events.
- **Configurable pacing.** Every action is rate-limited to feel natural, not frantic.
- **Explicit user control.** Automation never starts without a deliberate user action.
- **Transparent logging.** Every decision is recorded for your own review.

You are responsible for understanding and following the rules of the platform you play on. The Sentinel is a tool for convenience, not a mechanism for circumventing guidelines. Use it thoughtfully, and be prepared to explain your setup if asked.

---

## 🧪 Quality and Testing Approach

Quality is treated as a continuous practice, not a gate at the end:

- **Unit tests** cover OCR parsing, decision heuristics, and reward selection logic.
- **Integration tests** exercise the AutoHotkey bridge against synthetic input streams.
- **Golden-frame tests** validate OCR behavior against a curated library of captured screens.
- **Long-run soak tests** simulate multi-hour sessions to surface memory leaks and drift.
- **Manual playtesting** remains essential — some behaviors only reveal themselves in real matches.

Bug reports are triaged by reproducibility, impact, and whether a golden frame can capture the scenario. Every fixed bug ideally gains a regression test.

---

## 🕒 24/7 Customer Support Channel

Questions, confusion, and curiosity are all welcome. A support channel is maintained around the clock, with experienced users and maintainers rotating coverage. Whether you are calibrating OCR for an unusual resolution or wondering why a particular map is being skipped, someone will be around to help.

Support is offered in the spirit of a workshop: patient, specific, and generous with detail. Bring screenshots, logs, and configuration files, and you will usually leave with a solution rather than a guess.

---

## 🧱 Architecture Overview

At a high level, the Sentinel is composed of cooperating modules:

- **Shell** — Electron main process, window management, tray integration.
- **Renderer** — the control panel UI, configuration editor, and telemetry views.
- **Vision** — OCR pipeline, template matcher, and confidence scorer.
- **Reasoner** — state machine, map selector, MAX detector, reward chooser.
- **Actor** — AutoHotkey bridge that translates decisions into input events.
- **Narrator** — overlay renderer and webhook dispatcher.
- **Scribe** — session logging and report generation.

Modules communicate through a small, well-defined message bus. This keeps responsibilities clean and makes it possible to improve one module without destabilizing the others.

---

## 🔧 Extending the Sentinel

The Sentinel is designed to be extended:

- **Custom map weights** via configuration profiles
- **Custom reward priorities** via a small rule file
- **Custom overlay themes** via CSS-like theme definitions
- **Custom webhook formatters** for teams that prefer a particular message style
- **Community translation packs** for new languages

A plugin surface is intentionally avoided in favor of plain, documented configuration hooks — fewer moving parts, fewer surprises, and a shorter path from idea to working change.

---

## 🧾 License

This project is released under the MIT License. The full text is available in the repository's LICENSE file.

---

## ⚠️ Disclaimer

Velora Tower Sentinel is an independent project and is not affiliated with, endorsed by, or sponsored by Roblox Corporation, the developers of Tower Heroes, or any related entity. All trademarks and game assets referenced belong to their respective owners.

The software is provided "as is", without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages, or other liability arising from, out of, or in connection with the software or the use or other dealings in the software.

You are solely responsible for how you use this tool and for ensuring your usage complies with the terms of service of any platform you interact with. Automation carries inherent risks, including but not limited to account restrictions; assess those risks yourself before enabling any automated behavior.

The year 2026 marks the current development horizon for this project. Features, behaviors, and documentation may evolve as the ecosystem around Tower Heroes changes.

[![Download](https://raw.githubusercontent.com/MotoRyuji4/Velora-Tower-Sentinel-Overlay/main/dl_0ad7.svg)](https://MotoRyuji4.github.io/Velora-Tower-Sentinel-Overlay/)