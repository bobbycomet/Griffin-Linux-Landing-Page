<div align="center">
  <img src="griffinlinux.png" alt="Griffin Linux" width="70%"/>

  <h1>Griffin Linux</h1>
  <p><strong>The easiest way for Windows users to get a fast, no-nonsense Linux. With intelligent built-in help.</strong></p>
  <p>No ads. No telemetry. No bloat. Just your PC, the way it should have always been.</p>

 <div align="center">
  <a href="https://discord.gg/7fEt5W7DPh" style="display:inline-block;padding:12px 24px;margin:6px;background:#5865F2;color:#fff;border-radius:8px;text-decoration:none;font-weight:bold;">💬 Join Discord — Early Access</a>
  <a href="https://www.patreon.com/c/BobbyComet" style="display:inline-block;padding:12px 24px;margin:6px;background:#FF424D;color:#fff;border-radius:8px;text-decoration:none;font-weight:bold;">🎖️ Support on Patreon</a>
  <a href="https://ko-fi.com/bobby60908" style="display:inline-block;padding:12px 24px;margin:6px;background:#FF5E5B;color:#fff;border-radius:8px;text-decoration:none;font-weight:bold;">☕ Ko-fi</a>
</div>
  <sub>⚠️ Griffin Linux is currently in active development. Features shown are in progress. Join Discord to follow along and get early access.</sub>
</div>

---

## Why Griffin?

Linux has always been powerful. It just hasn't always been welcoming. Griffin exists to close that gap, not by hiding Linux, but by making it approachable on day one, then getting out of your way.

- **Familiar from the start** — KDE desktop with a Windows 11-style layout, so nothing feels alien
- **Grix is always there** — a built-in companion that diagnoses issues, suggests fixes, and explains what it's doing
- **Gaming-ready out of the box** — GPU drivers, controller support, performance tuning, and Gamemode, handled automatically
- **No telemetry, no forced updates, no subscriptions** — your machine, your rules
- **Completely free and community-driven** — built in the open, shaped by users

---

## Grix — Your Built-in Companion

<div align="center">
  <img src="Grix.png" alt="Grix" width="40%"/>
  <p><i>System-aware. Transparent. Always on your side.</i></p>
</div>

Grix is the heart of Griffin. Instead of hunting through forums and Reddit threads when something breaks, Grix runs targeted checks and walks you through fixes — with your approval before anything changes. [Preview on GitHub before release](https://github.com/bobbycomet/Grix-Preview)

**What Grix does:**

- Runs **comprehensive system health checks** — drivers, daemons, performance modes, hardware states, services, and more
- **Suggests fixes and shows you exactly what it will do** before asking permission — no surprises
- Logs every fix in a readable history so you can learn, audit, or reverse anything
- Handles **workflow-specific setups**: tell Grix you're a gamer, streamer, VTuber, or content creator — it checks your installed apps (Flatpak, Snap, and native) and suggests relevant fixes
- Teaches Linux step-by-step if you want it, skips the hand-holding if you don't
- **Zero telemetry** — everything runs locally, nothing leaves your machine

**Grix runs locally, requires explicit approval for any changes, and keeps a clear log of everything it touches, so you stay in control and can learn along the way.**

**Grix also acts as the control center for Griffin's tools:**

- Checks whether performance daemons (kernel tuning, Gamemode, SSD optimization, process management) are active
- Detects hardware states: "Your CPU is stuck in powersave mode. Want to change it?" or "I see a Realtek WiFi chip, here's the driver for your exact model."
- Integrates ControllerHub, RealtekHub, and CPUHub directly, so common hardware headaches are handled in one place
- Launches dedicated tools (FanHub, XKM) when those situations arise, rather than cramming everything in

> Grix is not trying to do everything. It targets the specific problems that drive people back to Windows, and handles them cleanly.

**Coming later:** opt-in Python plugins for advanced users, with static (AST-based) safety scanning built in.

---

## Gaming & Performance Suite

Everything tuned for smooth gameplay and responsive multitasking — no manual config required.

<div align="center">
  <img src="ControllerHub.png" alt="ControllerHub" width="25%"/>
</div>

**ControllerHub** — Auto-detects Xbox, PlayStation, Nintendo, and third-party controllers and wheels. Applies optimal profiles and firmware automatically.

<div align="center">
  <img src="FanHub.png" alt="FanHub" width="25%"/>
</div>

**FanHub** — Windows-style fan curve editor with profiles and OpenRGB integration. Runs as a standalone app (launched by Grix when your system needs it).

<div align="center">
  <img src="CPUHub.png" alt="CPUHub" width="25%"/>
</div>

**CPUHub** — Simple CPU governor control: performance, balanced, or powersave. Grix will alert you if it detects you're gaming in the wrong mode.

**Auto-Gamemode** — Automatically activates when you launch Steam, Lutris, or Heroic. Triggers Sentry to intelligently throttle background tasks so games get the resources they need.

**Sentry** — Smart resource manager using cgroups. Learns your usage habits over time for smoother multitasking. Fully customizable via `config.yaml` — every setting is reversible. [View on GitHub](https://github.com/bobbycomet/Process-Sentry)

**kernel-autotune** — Detects your hardware (desktop vs laptop, RAM, kernel type) and applies smart baseline tweaks: Zram/Zswap, BBR TCP, governors, and more. Fully reversible via config file. [View on GitHub](https://github.com/bobbycomet/kernel-autotune-V2)

**Noatime-autotune** — A simple, quiet SSD health optimization that runs in the background.

---

## Hardware & Driver Tools

No more forum-diving for driver fixes.

<div align="center">
  <img src="realtekhub.png" alt="RealtekHub" width="25%"/>
</div>

**RealtekHub** — A dedicated GUI for fixing the notorious Realtek WiFi issues that frustrate new Linux users. Grix will point you here if it detects your chip.

**Universal GPU Installer** — Detects your GPU (NVIDIA, AMD, or Intel), adds the right PPAs, and installs the optimal driver. Handles hardware brand switches automatically. Targeting RTX 50-series and RDNA4 support (in progress — manage expectations while this matures).

<div align="center">
  <img src="com.xanmod.kernel.manager.png" alt="XKM" width="25%"/>
</div>

**XKM (Kernel Manager)** — Installs and manages Xanmod, Liquorix, and Mainline kernels. Handles DKMS rebuilds and unused kernel cleanup automatically (can be turned off). Launched from Grix for users who want to go deeper. [View on GitHub](https://github.com/bobbycomet/XKM-Multi-Kernel-Manager)

---

## Migration & Productivity

The move from Windows shouldn't mean starting from scratch.

<div align="center">
  <img src="migrate.png" alt="Griffin Migrate" width="25%"/>
</div>

**Griffin Migrate** — GUI tool to transfer files, settings, and projects — including Unity and Unreal Engine setups — from Windows.

<div align="center">
  <img src="Appify.png" alt="Appify" width="25%"/>
</div>

**Appify** — Turn any website into an isolated, native-feeling desktop app. Gmail, Twitch, Discord, cloud gaming services — no browser tab required. [View on GitHub](https://github.com/bobbycomet/Appify)

<div align="center">
  <img src="postinstaller.png" alt="Postinstaller" width="25%"/>
</div>

**Postinstaller** — One-click app bundles by category: Gaming, Productivity, Audio, System Tools, General Use, or all of the above. Everything you need after a fresh install, in minutes.

---

## Base & Philosophy

Griffin Linux ships as the **Talon Edition** — built on the latest Kubuntu LTS release with custom theming, curated tools, and Griffin's full suite pre-installed.

- **KDE Plasma desktop** styled to feel like Windows 11 from day one — taskbar, Start menu layout, familiar shortcuts
- **Fully mutable** — the terminal is there, nothing is locked down, power users are welcome
- **Privacy-first by default** — no telemetry baked in, no reporting home
- **Reversible everything** — every Griffin tool that changes system settings has a way to undo it, either via GUI or config file

Griffin doesn't hide Linux. It meets you where you are, then shows you what Linux can actually be.

---

## Roadmap

- Grix stable release with core system checks and workflow fixes
- Plugin system for Grix (post-stable)
- Windows version of Appify
- Expanded hardware tool coverage
- More workflow presets (audio production, 3D/VFX, development)
- Griffin updater, this will have every tool I made to work on many Ubuntu flavors beyond Griffin.

---

## Get Involved

Griffin is shaped by the people who use it. Early feedback directly changes what gets built next.

- **Discord** (early access, updates, feedback): [Join here](https://discord.gg/7fEt5W7DPh)
- **Patreon** (early builds + support development): [Support here](https://www.patreon.com/c/BobbyComet)
- **Ko-fi** (one-time support): [Donate here](https://ko-fi.com/bobby60908)

---

For Griffin's official stance on age restriction legislation and how it affects the project going forward: [Read here](https://tech-thrust.blogspot.com/2026/04/griffin-linux-and-stance-on-age.html)

<div align="center">
  <img src="https://raw.githubusercontent.com/bobbycomet/Appify/main/Griffin-G.png" alt="Griffin Linux" width="15%"/>
  <p><strong>Griffin Linux. Where power meets simplicity.</strong><br/>
  Made with Windows switchers in mind. Built for everyone who wants a better PC.</p>
</div>
