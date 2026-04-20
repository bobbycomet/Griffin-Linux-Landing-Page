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

You get the same desktop, package managers, drivers, and upstreams you would have anyway, with a coordinated set of tools on top that handle the things that usually send new users to forums: hardware quirks, driver setup, gaming performance, audio issues, and system health.

Griffin is not trying to deliver magic. It is designed to reduce the need to troubleshoot and to make the first months of using Linux feel like using a finished system rather than assembling one.

An official installer for the full Griffin tool suite is planned, so you will be able to bring Griffin to any compatible Debian/Ubuntu system without starting from scratch.

---

## A note on platform direction

Griffin's primary focus is on Debian and Ubuntu-based systems. This is a deliberate choice for reliability and maintainability. That said, several tools have a broader reach by their nature:

- **Appify** works across distros; it only creates a `.pwa_manager` file and detects whether X11, Wayland, or another display server is in use.
- **WinBridge** has base support for KDE/Ubuntu/Kubuntu, with a plugin system that extends compatibility to other distros via community-contributed distro plugins.
- **Sentry v3** is designed to run on any systemd-based Linux system.

All other Griffin tools primarily target Debian/Ubuntu systems.

> **Regarding a standalone Griffin distro:** Griffin has moved from a distro to a layer due to US legislation around age verification that would create serious complications for shipping a full Linux distribution. If that legislation is reversed or fails to pass, a Griffin distro will be revisited as an option. The tools, the vision, and the experience remain exactly the same.

---

## How the pieces fit together

Griffin is not a single app or control panel. It is a set of focused tools that each handle one job well, built to cooperate without you having to wire them together.

**Sentry v3** watches running processes and learns your habits over time. Use an app regularly, and Sentry makes sure it is never throttled unless the system has no other choice. When it detects a gamemoded Steam launch via Game Tune Hub's wrappers, it automatically pulls back background processes to free up resources, while making sure tools like OBS are never touched so your stream stays smooth. Your current configuration is always visible inside Game Tune Hub; no file hunting required.

**Kernel Autotune** handles low-level kernel settings at boot: Zram/Zswap, BBR TCP, governors, HDD optimization, and more. Its configuration is accessible inside Game Tune Hub if you need to review or reapply settings. Every kernel installed through XKM is automatically configured by Kernel Autotune, so switching kernels never leaves your system in an untuned state. Noatime Autotune handles SSD health separately.

**Game Tune Hub** is where gaming performance comes together. It wraps Steam with Gamemode, Gamescope, and Mangohud without needing launch options, backs up your original Steam executable so everything is reversible, and gives you a single place to view and configure both Sentry v3 and Kernel Autotune settings.

**Griffin Hub** brings together Controller Hub, CPU Hub, GPU Hub, and WiFi Hub. GPU Hub includes a hardware swap feature: if you switch to a GPU from a different brand, hit swap, and it safely reverts to base drivers, removing extras like CUDA, NVENC, or AMD ROCm, so nothing is left behind to cause conflicts. Once your new GPU is installed, use GPU Hub to install the right driver stack and any extras your hardware supports.

**Fan Hub** stands alone. It is a deep rethinking of fan control on Linux, too large and complex to sit inside Griffin Hub. It handles fan curves, cooling profiles, liquidctl, OpenRGB (including AIOs, CPU fans, GPU fans, NVMe temps, RAM temps, and more), and runs headlessly by hooking into the OpenRGB server.

**Grix** handles everything that does not belong to a dedicated tool: PipeWire fixes, drive health checks, capacity warnings with plain-language steps, and a learn function that helps you understand what is happening and why. When Grix spots a problem, it either walks you through fixing it or asks if you want it handled automatically. Everything is logged, so you can review or undo it.

---

## Core tools

These are the tools that run quietly and keep everything working:

**Sentry v3** learns your usage habits and manages background resource usage via cgroups. Gaming sessions are detected automatically through Game Tune Hub, background processes are pulled back, and critical tools are never touched. Configurable and visible inside Game Tune Hub. Runs on any systemd-based Linux system. [View on GitHub](https://github.com/bobbycomet/Process-Sentry)

**Kernel Autotune** applies smart baseline tweaks at boot, handles HDD optimization, and automatically configures every kernel installed via XKM. Fully reversible, with settings accessible inside Game Tune Hub. [View on GitHub](https://github.com/bobbycomet/kernel-autotune-V2)

**Noatime Autotune** runs quietly in the background, handling SSD health optimization. Nothing to configure.

---

## Gaming and performance

**Game Tune Hub** wraps Steam with Gamemode, Gamescope, and Mangohud without needing per-game launch options. Your original Steam executable is backed up, so changes are always reversible. Sentry v3 and Kernel Autotune settings are both configurable here, in one place.

**WinBridge** automates Windows app workflows on Linux, combining ideas from Bottles and Lutris in a very different way. A profile system sets base Wine modules for your use case: games, modded games, productivity, creative work, and more. Additional modules can be added as needed. Plugin sandboxing is built in, with an AST-based tier system, so you choose how much protection each app gets. Includes a CLI and a plugin store for downloading community extensions. Base support targets KDE/Ubuntu/Kubuntu, with distro plugins available for other systems. Still in early development.

---

## Hardware and drivers

**Griffin Hub** houses Controller Hub, CPU Hub, GPU Hub, and WiFi Hub in one place.

**Controller Hub** auto-detects Xbox, PlayStation, Nintendo, and third-party controllers and wheels. Applies optimal profiles and firmware automatically. Xone and Xpad-noone are treated as a pair; conflicting drivers are blacklisted but swappable.

**CPU Hub** gives you simple governor control: performance, balanced, or powersave. Kernel Autotune sets the baseline; CPU Hub lets you override it whenever you want.

**GPU Hub** detects your GPU and manages your driver stack, including extras like CUDA, NVENC, and AMD ROCm. The hardware swap feature safely reverts to base drivers and removes extras when you switch GPU brands, so you can install the new stack cleanly. RTX 50-series and RDNA4 support is in progress.

**WiFi Hub** handles Realtek and Broadcom driver fixes via a dedicated GUI. Pairs well with an Xanmod kernel installed through XKM.

<div align="center">
  <img src="com.xanmod.kernel.manager.png" alt="XKM" width="25%"/>
</div>

**XKM (Kernel Manager)** installs and manages Xanmod, Liquorix, and Mainline kernels. Handles DKMS rebuilds and unused kernel cleanup automatically (can be turned off). Every kernel XKM installs is configured by Kernel Autotune. Grix can recover DKMS if something goes wrong. [View on GitHub](https://github.com/bobbycomet/XKM-Multi-Kernel-Manager)

<div align="center">
  <img src="FanHub.png" alt="FanHub" width="25%"/>
</div>

**Fan Hub** is a standalone rethinking of fan control on Linux. Fan curves, cooling profiles, liquidctl, and OpenRGB integration covering AIOs, CPU fans, GPU fans, NVMe temps, RAM temps, and more. Runs headlessly via the OpenRGB server, so RGB and fan control work without OpenRGB open.

---

## Migration and productivity

<div align="center">
  <img src="migrate.png" alt="Griffin Migrate" width="25%"/>
</div>

**Griffin Migrate** is a GUI tool for transferring files, settings, and projects from Windows, including Unity and Unreal Engine setups.

<div align="center">
  <img src="Appify.png" alt="Appify" width="25%"/>
</div>

**Appify** turns any website into an isolated, native-feeling desktop app: Gmail, Twitch, Discord, cloud gaming services, and more. Sentry v3 includes flags so cloud gaming apps are never throttled. Works across distros; detects your display server automatically. [View on GitHub](https://github.com/bobbycomet/Appify)

<div align="center">
  <img src="postinstaller.png" alt="Griffin Persona" width="25%"/>
</div>

**Griffin Persona** lets you define your workflow and builds your desktop around it. Choose from curated profiles: Gaming, Productivity, Audio, System Tools, Streaming, General Use, or all of the above. It detects your hardware, so GPU drivers and extras like NVENC, CUDA, or AMD ROCm can be installed as part of your setup. Not tied to a fresh install; run it any time to set up or expand your workflow. A VTubing profile is planned.

---

## Grix: system health and support

<div align="center">
  <img src="Grix.png" alt="Grix" width="40%"/>
  <p><i>System-aware. Transparent. Always on your side.</i></p>
</div>

Grix handles the things that fall outside dedicated tools; the issues that would otherwise send a new Linux user to forums or Reddit. It runs targeted checks, explains what it finds in plain language, and either walks you through a fix or asks if you want it handled. Everything is logged, so you can review or undo any change.

Grix covers: PipeWire audio fixes, drive health monitoring, capacity warnings with plain-language steps, general system warnings, and a learn function that explains what Grix is doing and why.

Grix is currently under a major rewrite to make it lighter, more predictable, and more reliable across varying kernels and tricky updates. The goal is a tool that surfaces real problems clearly, handles the ones it can, and teaches you about your system along the way. [Preview on GitHub](https://github.com/bobbycomet/Grix-Preview)

---

## Griffin Updater

Griffin comes with a dedicated updater for all of its tools. It checks each tool's GitHub repo for updates and lets you update from a simple GUI, no terminal required. There is no auto-update by design; you choose when to update, so you can wait and see how a release lands before committing.

If Griffin tools are not yet installed, Griffin Updater handles that too: click Install next to any tool, and it takes care of the rest. For tools available in both AppImage and Deb formats, choose your preference once, and the updater remembers it.

AppImage tools (Deb also available where noted): Appify, Game Tune Hub, WinBridge, Griffin Hub, Grix, Fan Hub, Griffin Persona, and Griffin Updater itself. XKM currently has a Deb package with an AppImage coming.

---

## Philosophy

- **Not hiding Linux:** Griffin meets you where you are and shows you what Linux can be, without locking anything down
- **Reversible by default:** Every Griffin tool that changes system settings can be undone, via GUI or config file
- **Privacy first:** no telemetry, no reporting home
- **Open and community-driven:** built in the open, shaped by the people who use it

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

Hi, I'm Bobby. I started out building my own tools and scripts; Griffin was never the original plan. I've been watching Linux since 1999, and I've used both Windows and Linux long enough to understand why the switch feels hard. Linux is powerful, but it's fragmented, and its culture can make newcomers feel like outsiders before they've even started.

Griffin came from a simple thought I had while working on Appify: shouldn't Linux be better at this? Not more powerful; it already is. Better at welcoming people in without making them feel like they have to earn it first.

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
