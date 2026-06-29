<div align="center">
  <img src="griffinlinux.png" alt="Griffin Linux" width="70%"/>

  <h1>Griffin Linux</h1>
  <p><strong>The easiest way for Windows users to get a fast, no-nonsense Linux experience. With intelligent built-in help.</strong></p>
  <p>No ads. No telemetry. No bloat. Just your PC, the way it should have always been.</p>

<div align="center">
  <a href="https://discord.gg/7fEt5W7DPh" style="display:inline-block;padding:12px 24px;margin:6px;background:#5865F2;color:#fff;border-radius:8px;text-decoration:none;font-weight:bold;">💬 Join Discord — Early Access</a>
  <a href="https://griffin-linux.blogspot.com/" style="display:inline-block;padding:12px 24px;margin:6px;background:#FF6600;color:#fff;border-radius:8px;text-decoration:none;font-weight:bold;">📝 Official Blog</a>
  <a href="https://www.patreon.com/c/BobbyComet" style="display:inline-block;padding:12px 24px;margin:6px;background:#FF424D;color:#fff;border-radius:8px;text-decoration:none;font-weight:bold;">🎖️ Support on Patreon</a>
  <a href="https://ko-fi.com/bobby60908" style="display:inline-block;padding:12px 24px;margin:6px;background:#FF5E5B;color:#fff;border-radius:8px;text-decoration:none;font-weight:bold;">☕ Ko-fi</a>
</div>
  <sub>⚠️ Griffin Linux is currently in active development. Features shown are in progress. Join Discord to follow along and get early access. Griffin is not affiliated with Ubuntu/Kubuntu or Canonical.</sub>
</div>

---

## What is Griffin?

Linux has always been powerful. It just hasn't always been welcoming. Griffin is a layer built on top of Debian/Ubuntu systems, designed to reduce the friction of moving from Windows without hiding what Linux actually is.

You get the same desktop, package managers, drivers, and upstreams you'd have anyway — plus a coordinated set of tools on top that handle the things that usually send new users to forums: hardware quirks, driver setup, gaming performance, audio issues, and system health.

Griffin isn't trying to deliver magic. It's designed to cut down on troubleshooting and make the first months of using Linux feel like using a finished system, not assembling one.

An official installer for the full Griffin tool suite is planned, so you'll be able to bring Griffin to any compatible Debian/Ubuntu system without starting from scratch.

---

## Platform direction

Griffin's primary focus is Debian and Ubuntu-based systems — a deliberate choice for reliability and maintainability. A few tools reach further by nature:

- **Appify** works across distros; it only creates a `.pwa_manager` file and detects whether you're on X11, Wayland, or something else.
- **WinBridge** has base support for KDE/Ubuntu/Kubuntu, with a plugin system that extends compatibility to other distros via community-contributed plugins. Many tools have been moved to WinBridge.
- **Sentry v3** runs on any systemd-based Linux system.

Everything else targets Debian/Ubuntu.

> **On a standalone Griffin distro:** Griffin moved from being a distro to being a layer because of US legislation around age verification, which would create serious complications for shipping a full Linux distribution. If that legislation is reversed or fails to pass, a Griffin distro is back on the table. The tools, the vision, and the experience stay exactly the same either way.

---

## How the pieces fit together

Griffin isn't one app or control panel — it's a set of focused tools that each handle one job well, built to cooperate without you having to wire anything together.

- **Sentry v3** watches what's running and learns your habits, pulling back background processes during gaming sessions while making sure tools like OBS are never touched.
- **Kernel Autotune** handles the low-level kernel settings — Zram/Zswap, BBR TCP, governors, HDD optimization — and automatically configures every kernel installed through XKM.
- **Game Tune Hub** brings it together for gaming: one place to wrap Steam in Gamemode/Gamescope/Mangohud and view your Sentry and Kernel Autotune settings.
- **Griffin Hub** brings hardware control — controllers, CPU, GPU, WiFi — into one place.
- **Fan Hub** stands on its own; fan and RGB control turned out to be too large to fit inside Griffin Hub.
- **Grix** catches everything else: PipeWire fixes, drive health, capacity warnings, and a learn function that explains what's happening and why.

Full details on each tool are below.

---

## Core tools

These run quietly in the background and keep everything else working.

**Sentry v3** — learns your usage habits and manages background resource use via cgroups. Detects gaming sessions automatically through Game Tune Hub, pulls back background processes, and never touches critical tools like OBS. Configurable and visible inside Game Tune Hub. Runs on any systemd-based Linux system. [View on GitHub](https://github.com/bobbycomet/Process-Sentry)

**Kernel Autotune** — applies smart baseline tweaks at boot, handles HDD optimization, and automatically configures every kernel installed via XKM. Fully reversible, with settings accessible inside Game Tune Hub. [View on GitHub](https://github.com/bobbycomet/kernel-autotune-V2)

---

## Gaming and performance

**Game Tune Hub — moved to WinBridge** — wraps Steam with Gamemode, Gamescope, and Mangohud; no per-game launch options required. Backs up your original Steam executable so changes are always reversible. Sentry v3 and Kernel Autotune settings are both configurable here, in one place.

**WinBridge** — automates Windows app workflows on Linux, combining ideas from Bottles and Lutris in a different way. A profile system sets base Wine modules for your use case — games, modded games, productivity, creative work, and more — and you can add modules as needed. Plugin sandboxing is built in, with an AST-based tier system so you choose how much protection each app gets. Includes a CLI and a plugin store for community extensions. Base support targets KDE/Ubuntu/Kubuntu, with distro plugins for other systems. Still in early development.

---

## Hardware and drivers

**Griffin Hub — moved to WinBridge** houses Controller Hub, CPU Hub, GPU Hub, and WiFi Hub in one place.

- **Controller Hub** — auto-detects Xbox, PlayStation, Nintendo, and third-party controllers and wheels, and applies optimal profiles and firmware automatically. Xone and xpad-noone are treated as a pair; conflicting drivers are blacklisted but swappable.
- **CPU Hub** — simple governor control: performance, balanced, or powersave. Kernel Autotune sets the baseline; CPU Hub lets you override it anytime.
- **GPU Hub** — detects your GPU and manages your driver stack, including extras like CUDA, NVENC, and AMD ROCm. The hardware swap feature safely reverts to base drivers and removes extras when you switch GPU brands, so you can install the new stack clean. RTX 50-series and RDNA4 support is in progress.
- **WiFi Hub** — handles Realtek and Broadcom driver fixes via a dedicated GUI. Pairs well with an Xanmod kernel installed through XKM.

<div align="center">
  <img src="com.xanmod.kernel.manager.png" alt="XKM" width="25%"/>
</div>

**XKM (Kernel Manager)** — installs and manages Xanmod, Liquorix, and Mainline kernels. Handles DKMS rebuilds and unused kernel cleanup automatically (can be turned off). Every kernel XKM installs is configured by Kernel Autotune. Grix can recover DKMS if something goes wrong. [View on GitHub](https://github.com/bobbycomet/XKM-Multi-Kernel-Manager)

<div align="center">
  <img src="FanHub.png" alt="FanHub" width="25%"/>
</div>

**Fan Hub** — a standalone rethinking of fan control on Linux: fan curves, cooling profiles, liquidctl, and OpenRGB integration covering AIOs, CPU fans, GPU fans, NVMe temps, RAM temps, and more. Runs headlessly via the OpenRGB server, so RGB and fan control work without OpenRGB open.

---

## Migration and productivity

<div align="center">
  <img src="migrate.png" alt="Griffin Migrate" width="25%"/>
</div>

**Griffin Migrate** — a GUI tool for transferring files, settings, and projects from Windows, including Unity and Unreal Engine setups.

<div align="center">
  <img src="Appify.png" alt="Appify" width="25%"/>
</div>

**Appify** — turns any website into an isolated, native-feeling desktop app: Gmail, Twitch, Discord, cloud gaming services, and more. Sentry v3 flags cloud gaming apps so they're never throttled. Works across distros and detects your display server automatically. [View on GitHub](https://github.com/bobbycomet/Appify)

<div align="center">
  <img src="postinstaller.png" alt="Griffin Persona" width="25%"/>
</div>

**Griffin Persona** — Griffin's welcome app. You pick one or more personas: Gaming, Productivity, Audio, System Tools, Streaming, General Use; each one is a complete workflow, and Persona configures your desktop to match. Pick a single persona, or select them all at once. It also detects your hardware, so GPU drivers and extras like NVENC, CUDA, or AMD ROCm install automatically as part of the setup. Not tied to a fresh install, run it any time to set up or expand a workflow. A VTubing persona is planned.

---

## Grix: system health and support

<div align="center">
  <img src="Grix.png" alt="Grix" width="40%"/>
  <p><i>System-aware. Transparent. Always on your side.</i></p>
</div>

Grix handles the things that fall outside dedicated tools — the issues that would otherwise send a new Linux user to forums or Reddit. It runs targeted checks, explains what it finds in plain language, and either walks you through a fix or asks if you want it handled. Everything is logged, so you can review or undo any change.

Grix covers: PipeWire audio fixes, drive health monitoring, capacity warnings with plain-language steps, general system warnings, and a learn function that explains what Grix is doing and why.

Grix is currently under a major rewrite to make it lighter, more predictable, and more reliable across varying kernels and tricky updates. The goal is a tool that surfaces real problems clearly, handles the ones it can, and teaches you about your system along the way. [Preview on GitHub](https://github.com/bobbycomet/Grix-Preview)

---

## Griffin Updater

Griffin ships with a dedicated updater for all of its tools. It checks each tool's GitHub repo for updates and lets you update from a simple GUI, no terminal required. There's no auto-update by design; you choose when to update, so you can see how a release lands before committing.

If a Griffin tool isn't installed yet, Griffin Updater handles that too. Click Install next to any tool, and it takes care of the rest. For tools available in both AppImage and Deb formats, choose your preference once, and the updater remembers it.

- **AppImage** (Deb also available where noted): Appify, Game Tune Hub, WinBridge, Griffin Hub, Grix, Fan Hub, Griffin Persona, Griffin Updater
- **Deb only (for now)**: XKM — AppImage coming

---

## Philosophy

- **Not hiding Linux** — Griffin meets you where you are and shows you what Linux can be, without locking anything down
- **Reversible by default** — every Griffin tool that changes system settings can be undone, via GUI or config file
- **Privacy first** — no telemetry, no reporting home
- **Open and community-driven** — built in the open, shaped by the people who use it

---

## Roadmap

- Grix stable release
- Official Griffin tool suite installer for Debian/Ubuntu systems
- Griffin Persona stable release
- Plugin system for Grix (post-stable)
- Windows version of Appify
- Expanded hardware tool coverage
- More workflow presets: audio production, 3D/VFX, development
- Griffin Updater with full install and update support across Ubuntu-based systems

---

## A bit about me

Hi, I'm Bobby. I started out building my own tools and scripts — Griffin was never the original plan. I've been watching Linux since 1999, and I've used both Windows and Linux long enough to understand why the switch feels hard. Linux is powerful, but it's fragmented, and its culture can make newcomers feel like outsiders before they've even started.

Griffin came from a simple thought I had while working on Appify: shouldn't Linux be better at this? Not more powerful — it already is. Better at welcoming people in, without making them feel like they have to earn it first.

That's what this is. Not a replacement for Windows. A replacement for the experience that drives people away from Linux before they ever see what it can do.

---

## Get involved

Griffin is shaped by the people who use it. Early feedback directly changes what gets built next.

- **Discord** (early access, updates, feedback): [Join here](https://discord.gg/7fEt5W7DPh)
- **Official Blog** (project news and updates): [Read here](https://griffin-linux.blogspot.com/)
- **Patreon** (early builds + support development): [Support here](https://www.patreon.com/c/BobbyComet)
- **Ko-fi** (one-time support): [Donate here](https://ko-fi.com/bobby60908)

---

For Griffin's official stance on age restriction legislation and how it affects the project going forward: [Read here](https://tech-thrust.blogspot.com/2026/04/griffin-linux-and-stance-on-age.html)

<div align="center">
  <img src="https://raw.githubusercontent.com/bobbycomet/Appify/main/Griffin-G.png" alt="Griffin Linux" width="15%"/>
  <p><strong>Griffin Linux. Where power meets simplicity.</strong><br/>
  Made with Windows switchers in mind. Built for everyone who wants a better PC.</p>
</div>
