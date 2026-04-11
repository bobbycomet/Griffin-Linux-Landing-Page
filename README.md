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

---
# Mission statement:

**The mission is very simple. Make Linux usable by everyone, while keeping the soul of Linux. I'm not out to fix every possible failure point; that would be nearly impossible as Linux grows and upstream changes.**

**Switching to Linux shouldn’t feel like rebuilding your computer from scratch.**

**Griffin exists to make the move from Windows feel natural, safe, and frustration-free, while keeping everything that makes Linux powerful.**

**Most people don’t leave Windows because they suddenly want to become Linux experts.**
They leave because they want control, privacy, performance, and a computer that feels like it belongs to them again.**

**Griffin is designed for that.**

**Instead of spending your first weeks fixing drivers, hunting through forums, and learning terminal commands just to make your PC usable, Griffin gives you a system that already understands your hardware, your workflows, and the things you actually want to do.**

**Gaming. Streaming. Creating. Everyday computing.**

**Linux stays powerful and fully open.**
**But the first experience finally feels simple.**

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
## What this means for you

On most Linux systems, you become the system failure investigator.

You install tools, configure services, read guides, and slowly build a setup that works for your hardware and your workflow. Over time, you learn how the pieces fit together.

Griffin changes that experience.

Instead of becoming the investigator, you start with a system that already knows how its pieces fit:

- When you install a GPU driver, the performance tools already know it exists.
- When you launch a game, the system already knows what should pause and what should stay running.
- When a background service fails silently, you don’t discover it weeks later; you get told immediately.
- Grix is the layer that handles all the hard stuff

You’re not learning Linux by fixing problems.
You’re learning Linux while using a computer that already works.

That difference sounds small, but it completely changes the first couple of months of using Linux.

Griffin is designed so your first experience feels like using a finished operating system, not assembling one.

---

# How Griffin Works
Griffin is a platform, not a bundle of tools

Most Linux setups are a collection of independent utilities.
You install tools one by one, hope they don’t conflict, and troubleshoot when something silently stops working.

Griffin is designed differently.

Every core component is built to work together as one coordinated system, with Grix acting as the control center.

The Griffin Architecture (Simple View)

Griffin is built in layers that cooperate with each other:

1) The Foundation — Stable, familiar Linux

Griffin Talon Edition is built on Kubuntu LTS with KDE Plasma.
You get long-term stability and a desktop that feels familiar from day one.

2) The Automation Layer — Quiet background tuning

Several lightweight services continuously keep your system optimized:

- Process Sentry manages background resource usage
- Kernel Autotune applies smart baseline performance tweaks
- Noatime Autotune protects SSD health
- Gamemode activates automatically when you play

These tools run quietly, so you don’t have to think about them.

3) The Hardware Layer — Dedicated problem solvers

When hardware needs attention, Griffin provides focused tools designed for specific jobs:

- ControllerHub for game controllers and wheels
- FanHub for fan curves and cooling
- CPU Hub for power and performance modes
- WiFi Hub for Realtek and Broadcom fixes
- GPU Hub for driver management and hardware swaps
- XKM for advanced kernel management

Each tool is specialized instead of being crammed into one giant app.

4) The Workflow Layer — Living and working in Linux

Griffin also includes tools that help you move in and stay productive:

- Griffin Migrate moves your files and projects from Windows
- Appify turns web apps into native desktop apps
- Postinstaller installs curated software bundles in minutes

5) Grix — The Control Center

Grix sits above everything.

Instead of forcing you to hunt through settings and forums, Grix:

- Watches system health
- Detects hardware and workflow states
- Checks whether background services are running correctly
- Suggests fixes and explains them before making changes
- Launches the right tool when it’s needed
- Keeps a readable history of every change

Grix doesn’t try to replace the tools.
It connects them and makes them work together.

Why this matters

Typical Linux troubleshooting looks like this:

Install multiple tools manually
Hope they start on boot
Hope they don’t conflict
Search forums when something breaks

Griffin replaces that experience with a coordinated system that:

- knows what tools are installed
- knows what should be running
- knows what you’re trying to do
- helps when something isn’t right

Griffin isn’t just preconfigured.
It’s designed to keep working.
---

## Gaming & Performance Suite

Everything tuned for smooth gameplay and responsive multitasking — no manual config required.

<div align="center">
  <img src="ControllerHub.png" alt="ControllerHub" width="25%"/>
</div>

**Controller Hub** — Auto-detects Xbox, PlayStation, Nintendo, and third-party controllers and wheels. Applies optimal profiles and firmware automatically. Moved to Grix, and has the same logic. Xone and Xpad-noone are treated as a pair; all others that conflict will be blacklisted, but can be swapped in Grix.

<div align="center">
  <img src="FanHub.png" alt="FanHub" width="25%"/>
</div>

**FanHub** — Windows-style fan curve editor with profiles and OpenRGB integration. Runs as a standalone app (launched by Grix when your system needs it).

<div align="center">
  <img src="CPUHub.png" alt="CPUHub" width="25%"/>
</div>

**CPU Hub** — Simple CPU governor control: performance, balanced, or powersave. Grix will alert you if it detects you're gaming in the wrong mode, switches to the one you need, and you can switch to the mode you want any time with performance, powersave, balanced, and so on profiles. 

**Auto-Gamemode** — Automatically activates when you launch Steam, Lutris, or Heroic. Triggers Sentry to intelligently throttle background tasks so games get the resources they need. This works with Process Sentry. Sentry will see you gaming, it slows down other processes, except for things like OBS and other curated software, so streamers still get performance in both, so you get all the performance, none of the "oops I throttled your stream." Planned to be a part of Grix for a start button if it fails silently.

**Sentry** — Smart resource manager using cgroups. Learns your usage habits over time for smoother multitasking. Fully customizable via `config.yaml` — every setting is reversible. Planned to be a part of Grix later for configuration, and a start button if the daemon fails. [View on GitHub](https://github.com/bobbycomet/Process-Sentry)

**kernel-autotune** — Detects your hardware (desktop vs laptop, RAM, kernel type) and applies smart baseline tweaks: Zram/Zswap, BBR TCP, governors, and more. Fully reversible via config file. Planned to be a part of Grix later for configuring and to check if it is working, with a button to start it if it fails at boot. [View on GitHub](https://github.com/bobbycomet/kernel-autotune-V2)

**Noatime-autotune** — A simple, quiet SSD health optimization that runs in the background.

---

## Hardware & Driver Tools

No more forum-diving for driver fixes.

**WIFI Hub** — A dedicated GUI for fixing the notorious Realtek WiFi issues that frustrate new Linux users. Grix will point you here if it detects your chip. Moved to be a part of Grix, which includes Broadcom drivers as well.

**GPU HUB** — Grix now detects your GPU (NVIDIA, AMD, or Intel), adds the right PPAs, and installs the optimal driver. Handles hardware brand switches by clicking "hardware swap", and it reverts to the basic drivers, so when you turn off, install the GPU, and boot back in, Grix sees the switch. Targeting RTX 50-series and RDNA4 support (in progress — manage expectations while this matures).

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

**Griffin Migrate** — GUI tool to transfer files, settings, and projects, including Unity and Unreal Engine setups, from Windows.

<div align="center">
  <img src="Appify.png" alt="Appify" width="25%"/>
</div>

**Appify** — Turn any website into an isolated, native-feeling desktop app. Gmail, Twitch, Discord, cloud gaming services — no browser tab required. Process Sentry has flags to not slow down the cloud service games. [View on GitHub](https://github.com/bobbycomet/Appify)

<div align="center">
  <img src="postinstaller.png" alt="Postinstaller" width="25%"/>
</div>

**Postinstaller** — One-click app bundles by category: Gaming, Productivity, Audio, System Tools, streaming, General Use, or all of the above. Everything you need after a fresh install, in minutes. Vtubing is a profile planned to be added soon.

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

## A bit about me:

**Hi, I'm Bobby, and I was not originally planning on building Griffin. I started out by just making my own tools and scripts. Griffin was never the plan. I saw the early days of Linux back in 1999. I remember the early X11 issues, and even though Linux has come a very long way, it is still terminal-first. Ecosystems have a mental model of how Linux should be for them, and companies have their own interests they have to think about. I remember the 20-year-old promise made by Windows, and watched as they became a data farm. One day, while I was developing Appify, I came to a thought, "Shouldn't Linux be better?" Linux is powerful, and yet, it is fragmented; it has a culture based on the distro you choose. That is not welcoming to what Linux is or can be. So, I started looking into distros, what they provide, and what users love. That is why Griffin came to be. I used both Windows and Linux (I use Linux only now), so I know what the issues are in both, and why Linux scares you away. Griffin is here to make Linux feel like it is not so hard; it is here to make Linux a better OS, it is here not to replace Windows, but to replace an experience.**

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
