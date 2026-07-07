<div align="center">
  <img src="griffinlinux.png" alt="Griffin Linux" width="70%"/>

  <h1>Griffin Linux</h1>
  <p><strong>Linux that feels like Windows, but faster, smarter, and it actually teaches you how to use it.</strong></p>
  <p>No ads. No telemetry. No bloat. Just your PC, the way it should have always been.</p>

<div align="center">
  <a href="https://discord.gg/7fEt5W7DPh" style="display:inline-block;padding:16px 32px;margin:6px;background:#5865F2;color:#fff;border-radius:8px;text-decoration:none;font-weight:bold;font-size:1.1em;">💬 Join Discord — Get Early Access</a>
  <a href="#overview" style="display:inline-block;padding:16px 32px;margin:6px;background:#2b2b2b;color:#fff;border-radius:8px;text-decoration:none;font-weight:bold;font-size:1.1em;">↓ Learn More</a>
</div>

<div align="center">
  <a href="https://griffin-linux.blogspot.com/" style="display:inline-block;padding:8px 18px;margin:4px;background:#FF6600;color:#fff;border-radius:8px;text-decoration:none;font-weight:bold;font-size:0.9em;">📝 Official Blog</a>
  <a href="https://www.patreon.com/c/BobbyComet" style="display:inline-block;padding:8px 18px;margin:4px;background:#FF424D;color:#fff;border-radius:8px;text-decoration:none;font-weight:bold;font-size:0.9em;">🎖️ Support on Patreon</a>
  <a href="https://ko-fi.com/bobby60908" style="display:inline-block;padding:8px 18px;margin:4px;background:#FF5E5B;color:#fff;border-radius:8px;text-decoration:none;font-weight:bold;font-size:0.9em;">☕ Ko-fi</a>
</div>

  <sub>⚠️ Griffin Linux tools have been released. Some features shown are in progress. Join Discord to follow along and get early access. Griffin is not affiliated with Ubuntu/Kubuntu or Canonical.</sub>
</div>

---

<div align="center">

**[Overview](#overview)** &nbsp;·&nbsp; **[Tools](#tools)** &nbsp;·&nbsp; **[Philosophy](#philosophy)** &nbsp;·&nbsp; **[Get Involved](#get-involved)**

</div>

---

<a id="overview"></a>
## What is Griffin?

Linux has always been powerful. It just hasn't always been welcoming. Griffin is a layer built on top of Debian/Ubuntu systems, designed to reduce the friction of moving from Windows without hiding what Linux actually is.

You get the same desktop, package managers, drivers, and upstreams you'd have anyway, plus a coordinated set of tools on top that handle the things that usually send new users to forums: hardware quirks, driver setup, gaming performance, audio issues, and system health.

Griffin isn't trying to deliver magic. It's designed to cut down on troubleshooting and make the first months of using Linux feel like using a finished system, not assembling one.

An official installer for the full Griffin tool suite is planned, so you'll be able to bring Griffin to any compatible Debian/Ubuntu system without starting from scratch.

---

## Platform direction

Griffin's primary focus is Debian and Ubuntu-based systems, a deliberate choice for reliability and maintainability. A few tools reach further by nature:

- **Appify** works across distros; it only creates a `.appify` file and detects whether you're on X11, Wayland, or something else.
- **Sentry v3** runs on any systemd-based Linux system.

Everything else targets Debian/Ubuntu.

> **On a standalone Griffin distro:** Griffin is a layer that acts as a unifier for many different things that would typically need the terminal. A Distro for Griffin is in the works now that much of the geopolitics has since been cleared up. As for the tools, they can be dropped into almost any Ubuntu-based distro. Griffin primarily distributes its tools as AppImages. This allows a single build to work across supported Ubuntu-based distributions without requiring users to add third-party repositories or manage repository keys. Griffin Updater provides centralized installation and updates, giving a consistent experience while keeping the base system's package sources unchanged. No release date for the distro as of now.

---

<a id="tools"></a>
## How the pieces fit together

Griffin isn't one app or control panel; it's a set of focused tools that each handle one job well, built to cooperate without you having to wire anything together.

- **Sentry v3** watches what's running and learns your habits, pulling back background processes during gaming sessions while making sure tools like OBS are never touched. It has flags to ignore anything Appify creates, and if you use Griffin Hub with System Tune to wrap Steam so Gamemode, gamescope, and mangohud can be run (removes the need for launch options with these 3), Sentry will prioritize the game.
- **Kernel Autotune** handles the low-level kernel settings, Zram/Zswap, BBR TCP, governors, HDD optimization, and automatically configures every kernel installed through XKM. It creates a config that can be edited and a state.json that is seen by other applications for system information and hardware information.
- **System Tune** evolved from Game Tune Hub and brings the system together for gaming: one place to wrap Steam in Gamemode/Gamescope/Mangohud and view your Sentry and Kernel Autotune settings, and you can configure them. If Kernel Autotune is not installed, a new tab is used that replicates what Kernel Autotune does, but not to the full extent.
- **Hardware Hub** brings hardware control, GitHub and stock kernel controllers (GitHub controllers: Xone, xpadneo, paroj/xpad, sim wheels with hid-tmff2), CPU, GPU, and WiFi (fixes Broadcom and Realtek common driver issues) into one place. Also a part of Griffin Hub.
- **Fan Hub** stands on its own; fan and RGB control turned out to be too large to fit inside Griffin Hub. It replicates a Windows-like experience with fan control and RGB control.
- **Grix** catches everything else: PipeWire fixes, drive health, capacity warnings, and a learn function that explains what's happening and why. Grix reads the `state.json` and gives you the system information in the GUI.
- **Griffin Updater** evolved from Discord Updater. Checks an `apps.json` for a catalog, checks version numbers of debs/AppImages that are not in official apt repos and updates them accordingly.

Full details on each tool are below.
```ascii
                                      
                          ┌──────────────────────────────┐
                          │        Griffin Linux         │
                          └──────────────┬───────────────┘
                                  Griffin Updater
               ┌─────────────────────────┼─────────────────────────┐
               │                         │                         │
         Griffin Hub              Griffin Persona                Grix
               │                         │                         │
       ┌───────┴───────┐         ┌───────┴───────┐         ┌───────┴───────┐
       │               │         │               │         │               │
 Hardware           Drivers   Initial Setup     Gaming    Learning      Troubleshooting
       │               │                         │            │
                    Diagnostics                 Profiles    
                          │
               ┌──────────┴──────────┐
               │                     │
         Kernel Autotune           Sentry
```
---

## Core tools

These run quietly in the background and keep everything else working.

**[Sentry v3](https://github.com/bobbycomet/Process-Sentry)** learns your usage habits and manages background resource use via cgroups. Detects gaming sessions automatically through Game Tune Hub, pulls back background processes, and never touches critical tools like OBS. Configurable and visible inside Game Tune Hub. Runs on any systemd-based Linux system.

**[Kernel Autotune](https://github.com/bobbycomet/kernel-autotune-V2)** applies smart baseline tweaks at boot, handles HDD optimization, and automatically configures every kernel installed via XKM. Fully reversible, with settings accessible inside Game Tune Hub.

---

## Hardware and drivers: Gaming and performance

**[Griffin Hub](https://github.com/bobbycomet/Griffin-Hub)** houses Controller Hub, CPU Hub, GPU Hub, and WiFi Hub in one place. Following the retirement of the standalone WinBridge tool, Wine automation was dropped. WinBridge's Wine automation didn't scale the way it needed to, so that work is being folded into Griffin Hub instead.

- **Dashboard** has graphs, temps, and more. This is an at-a-glance dashboard and does not replace KDE's system monitor.
- **System Tune** wraps Steam with Gamemode, Gamescope, and Mangohud; no per-game launch options required. Backs up your original Steam executable so changes are always reversible. Sentry v3 and Kernel Autotune settings are both configurable here, in one place.
- **Controller Hub** auto-detects Xbox, PlayStation, Nintendo, and third-party controllers and wheels, and applies optimal profiles and firmware automatically. Xone and xpad-noone are treated as a pair; conflicting drivers are blacklisted but swappable.
- **CPU Hub** simple governor control: performance, balanced, or powersave. Kernel Autotune sets the baseline; CPU Hub lets you override it anytime.
- **GPU Hub** detects your GPU and manages your driver stack, including extras like CUDA, NVENC, and AMD ROCm. The hardware swap feature safely reverts to base drivers and removes extras when you switch GPU brands, so you can install the new stack clean. RTX 50-series and RDNA4 support is in progress.
- **WiFi Hub** handles Realtek and Broadcom driver fixes via a dedicated GUI. Pairs well with an Xanmod kernel installed through XKM.

<img width="1920" height="1080" alt="Screenshot_20260705_120157" src="https://github.com/user-attachments/assets/88ba64be-fe09-4b2d-9fb7-30d076566589" />
<img width="1920" height="1080" alt="Screenshot_20260705_120145" src="https://github.com/user-attachments/assets/4c4dc25c-4505-4838-815d-6683272630ca" />
<img width="1920" height="1080" alt="Screenshot_20260705_120139" src="https://github.com/user-attachments/assets/5eee0459-4c62-4e62-8b90-4c6dca0b227d" />
<img width="1920" height="1080" alt="Screenshot_20260705_120126" src="https://github.com/user-attachments/assets/ff74f7e4-61f2-422c-a9b3-cd56b6c2b5bd" />
<img width="1920" height="1080" alt="Screenshot_20260705_120108" src="https://github.com/user-attachments/assets/d8eeba06-4076-4463-bd67-9ca1e06a1062" />
<img width="1920" height="1080" alt="Screenshot_20260705_120102" src="https://github.com/user-attachments/assets/90b98e55-0311-4c79-8f2e-1e4b28325a48" />
<img width="1920" height="1080" alt="Screenshot_20260705_120043" src="https://github.com/user-attachments/assets/7c92c07d-5f09-423f-8a79-76e3f1b78015" />
<img width="1920" height="1080" alt="Screenshot_20260705_120038" src="https://github.com/user-attachments/assets/6003c29f-151b-4017-a28d-2f91c5ffaca5" />
<img width="1920" height="1080" alt="Screenshot_20260705_120033" src="https://github.com/user-attachments/assets/40887bab-f2fa-41f9-885b-fea8fb637bf6" />
<img width="1920" height="1080" alt="Screenshot_20260705_120027" src="https://github.com/user-attachments/assets/756fc11f-ff8a-4318-b012-0402dc5f5b15" />
<img width="1920" height="1080" alt="Screenshot_20260705_120014" src="https://github.com/user-attachments/assets/8189cafd-dcb0-465e-9bb1-4e7e70e38a01" />
<img width="1920" height="1080" alt="Screenshot_20260705_120005" src="https://github.com/user-attachments/assets/95a93150-bd2b-4609-9874-4128300c7752" />


<div align="center">
  <img src="com.xanmod.kernel.manager.png" alt="XKM" width="25%"/>
</div>

**[XKM](https://github.com/bobbycomet/XKM-Multi-Kernel-Manager) (Kernel Manager)** installs and manages Xanmod, Liquorix, and Mainline kernels. Handles DKMS rebuilds and unused kernel cleanup automatically (can be turned off). Every kernel XKM installs is configured by Kernel Autotune. Grix can recover DKMS if something goes wrong. [View on GitHub](https://github.com/bobbycomet/XKM-Multi-Kernel-Manager)

<img width="1920" height="1080" alt="Screenshot_20260705_115852" src="https://github.com/user-attachments/assets/b6f78ee4-9dd2-40e3-a806-71c41d395ce7" />
<img width="1920" height="1080" alt="Screenshot_20260705_115841" src="https://github.com/user-attachments/assets/79bcf2e9-5987-4ae6-9a65-5055801a0746" />
<img width="1920" height="1080" alt="Screenshot_20260705_115832" src="https://github.com/user-attachments/assets/84b1359b-3093-4081-8faf-a4bb9eca7481" />


<div align="center">
  <img src="FanHub.png" alt="FanHub" width="25%"/>
</div>

**[Fan Hub](https://github.com/bobbycomet/Fan-Hub)** — a standalone rethinking of fan control on Linux: fan curves, cooling profiles, liquidctl, and OpenRGB integration covering AIOs, CPU fans, GPU fans, NVMe temps, RAM temps, and more. Runs headlessly via the OpenRGB server, so RGB and fan control work without OpenRGB open.

<img width="1920" height="1080" alt="Screenshot_20260705_115557" src="https://github.com/user-attachments/assets/2c252f86-7f9e-4a7f-9fb7-fb321312a53c" />
<img width="1920" height="1080" alt="Screenshot_20260705_115523" src="https://github.com/user-attachments/assets/3d9cb89b-9bc9-4a02-826d-24e2ee03858f" />
<img width="1920" height="1080" alt="Screenshot_20260705_115509" src="https://github.com/user-attachments/assets/634ba042-5500-4882-8bf1-16ea762b0030" />
<img width="1920" height="1080" alt="Screenshot_20260705_115451" src="https://github.com/user-attachments/assets/fd284389-a418-4577-8e23-3ac89d3945c8" />
<img width="1920" height="1080" alt="Screenshot_20260705_115443" src="https://github.com/user-attachments/assets/b30d5c64-b52a-4a87-8887-2a17c6095402" />
<img width="1920" height="1080" alt="Screenshot_20260705_115432" src="https://github.com/user-attachments/assets/7c655172-9502-4168-98ae-1aad98ea4e1a" />
<img width="1920" height="1080" alt="Screenshot_20260705_115419" src="https://github.com/user-attachments/assets/4ebf3441-9f36-4b84-a3de-4ea33d1aa8bc" />
<img width="1920" height="1080" alt="Screenshot_20260705_115337" src="https://github.com/user-attachments/assets/7192dac5-5bcd-4fd0-a210-baa2ace02bab" />
<img width="1920" height="1080" alt="Screenshot_20260705_115327-1" src="https://github.com/user-attachments/assets/7b5d5c51-00ea-4634-954a-e730467f33fc" />
<img width="1920" height="1080" alt="Screenshot_20260705_115319" src="https://github.com/user-attachments/assets/6b52b178-4e63-43ec-a6f8-f27438bf6732" />
<img width="1920" height="1080" alt="Screenshot_20260705_115216" src="https://github.com/user-attachments/assets/9885b438-4d00-41c0-ac1b-66cf50684d94" />


---

## Productivity

<div align="center">
  <img src="Appify.png" alt="Appify" width="25%"/>
</div>

**[Appify](https://github.com/bobbycomet/Appify)** — turns any website into an isolated, native-feeling desktop app: Gmail, Twitch, Discord, cloud gaming services, and more. Sentry v3 flags cloud gaming apps so they're never throttled. Works across distros and detects your display server automatically. [View on GitHub](https://github.com/bobbycomet/Appify)

<img width="1920" height="1080" alt="Screenshot_20260703_053801" src="https://github.com/user-attachments/assets/7d0b29b3-70fd-4a31-a03c-a1c1b1962d8f" />
<img width="1920" height="1080" alt="Screenshot_20260703_053734" src="https://github.com/user-attachments/assets/af3dc7b0-45e5-4322-a994-cae64cf61554" />
<img width="1920" height="1080" alt="Screenshot_20260703_053655" src="https://github.com/user-attachments/assets/2dcf078d-b08d-4ca2-9f1a-deba6b6ba5c7" />


<div align="center">
  <img width="300" height="300" alt="GriffinPersona" src="https://github.com/user-attachments/assets/0ac35f56-5176-43a5-a654-def31d4e0ef8" width="40%"/>
</div>

**Griffin Persona** — Griffin's welcome app. You pick one or more personas: Gaming, Productivity, Audio, System Tools, Streaming, General Use; each one is a complete workflow, and Persona configures your desktop to match. Pick a single persona, or select them all at once. It also detects your hardware, so GPU drivers and extras like NVENC, CUDA, or AMD ROCm install automatically as part of the setup. Not tied to a fresh install, run it any time to set up or expand a workflow. A VTubing persona is planned.

<img width="1920" height="1080" alt="Screenshot_20260701_070724" src="https://github.com/user-attachments/assets/7b6e12ed-4196-4008-a2a7-ff6c39cfdc5e" />
<img width="1920" height="1080" alt="Screenshot_20260630_023745" src="https://github.com/user-attachments/assets/cf4eba63-c0dc-46d8-904b-6f6453cec9fa" />
<img width="1920" height="1080" alt="Screenshot_20260630_023656" src="https://github.com/user-attachments/assets/4610fa3a-bb22-49bb-85ec-9737c6466771" />
<img width="1920" height="1080" alt="Screenshot_20260627_121916" src="https://github.com/user-attachments/assets/93bddcb2-aaa4-4340-af67-947bad961e20" />
<img width="1920" height="1080" alt="Screenshot_20260625_015650" src="https://github.com/user-attachments/assets/fe9fc625-8b3c-42a1-ae9d-8d114e7dc0bd" />
<img width="1920" height="1080" alt="Screenshot_20260625_015537" src="https://github.com/user-attachments/assets/059324a2-de53-42a6-85ef-042a058ac4df" />


---

## [Grix](https://github.com/bobbycomet/Grix): system health and support

<div align="center">
  <img src="Grix.png" alt="Grix" width="40%"/>
  <p><i>System-aware. Transparent. Always on your side.</i></p>
</div>

Grix handles the things that fall outside dedicated tools — the issues that would otherwise send a new Linux user to forums or Reddit. It runs targeted checks, explains what it finds in plain language, and either walks you through a fix or asks if you want it handled. Everything is logged, so you can review or undo any change.

Grix covers: PipeWire audio fixes, drive health monitoring, capacity warnings with plain-language steps, general system warnings, and a learn function that explains what Grix is doing and why.

Grix is currently under a major rewrite to make it lighter, more predictable, and more reliable across varying kernels and tricky updates. The goal is a tool that surfaces real problems clearly, handles the ones it can, and teaches you about your system along the way. [Preview on GitHub](https://github.com/bobbycomet/Grix-Preview)

<img width="1920" height="1080" alt="Screenshot_20260622_050511" src="https://github.com/user-attachments/assets/15203761-3bf6-4f61-9d69-be1052815adb" />
<img width="1920" height="1080" alt="Screenshot_20260622_050459" src="https://github.com/user-attachments/assets/778a5cb4-f406-4cfd-b07a-1aaeb0fb4aa2" />
<img width="1920" height="1080" alt="Screenshot_20260622_050445" src="https://github.com/user-attachments/assets/445037d8-5f52-4ce6-804f-fc25b4c50ab2" />
<img width="1920" height="1080" alt="Screenshot_20260622_050408" src="https://github.com/user-attachments/assets/9eefe039-4239-42b1-9474-9541c09acc5c" />
<img width="1920" height="1080" alt="Screenshot_20260622_050319" src="https://github.com/user-attachments/assets/ee41b4a0-e46b-41c2-9bf0-7cc37d474d27" />
<img width="1920" height="1080" alt="Screenshot_20260622_050311" src="https://github.com/user-attachments/assets/42b535bc-5910-48d9-b852-b7691b188471" />
<img width="1920" height="1080" alt="Screenshot_20260622_050256" src="https://github.com/user-attachments/assets/db0e029e-a61c-483f-82b5-129449c07bf0" />
<img width="1920" height="1080" alt="Screenshot_20260622_050244" src="https://github.com/user-attachments/assets/e51aa8ed-18b4-40e9-9cf0-c4ef0476a408" />
<img width="1920" height="1080" alt="Screenshot_20260622_050152" src="https://github.com/user-attachments/assets/e781d6b7-0807-4d21-ad6c-d4e75a5fd5b3" />
<img width="1920" height="1080" alt="Screenshot_20260705_114542" src="https://github.com/user-attachments/assets/8458325d-84ea-4594-84de-722610bab54d" />
<img width="1920" height="1080" alt="Screenshot_20260705_114523" src="https://github.com/user-attachments/assets/14098718-d2db-40d8-8ae5-4a05fe38d1d1" />

---

## [Griffin Updater](https://github.com/bobbycomet/GriffinUpdater)

Griffin ships with a dedicated updater for all of its tools. It checks each tool's GitHub repo for updates and lets you update from a simple GUI, no terminal required. There's no auto-update by design; you choose when to update, so you can see how a release lands before committing.

If a Griffin tool isn't installed yet, Griffin Updater handles that too. Click Install next to any tool, and it takes care of the rest. For tools available in both AppImage and Deb formats, choose your preference once, and the updater remembers it.

- **AppImage** (Deb also available where noted): Appify, Griffin Hub, Grix, Fan Hub, Griffin Updater, XKM
- **Deb only (for now)**: Griffin Persona, Sentry, Kernel Autotune

<img width="1920" height="1080" alt="Screenshot_20260705_102109" src="https://github.com/user-attachments/assets/3d746432-5077-4a36-9b0e-96358928af93" />
<img width="1920" height="1080" alt="Screenshot_20260705_102056" src="https://github.com/user-attachments/assets/fe0c9a88-b50b-4dec-9cc5-f45673696ef6" />

---

<a id="philosophy"></a>
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

Hi, I'm Bobby. I started out building my own tools and scripts; Griffin was never the original plan. I've been watching Linux since 1999, and I've used both Windows and Linux long enough to understand why the switch feels hard. Linux is powerful, but it's fragmented, and its culture can make newcomers feel like outsiders before they've even started.

Griffin came from a simple thought I had while working on Appify: shouldn't Linux be better at this? Not more powerful, it already is. Better at welcoming people in, without making them feel like they have to earn it first.

That's what this is. Not a replacement for Windows. A replacement for the experience that drives people away from Linux before they ever see what it can do.

---

<a id="get-involved"></a>
## Get involved

Griffin is shaped by the people who use it. Early feedback directly changes what gets built next.

<div align="center">
  <a href="https://discord.gg/7fEt5W7DPh" style="display:inline-block;padding:16px 32px;margin:6px;background:#5865F2;color:#fff;border-radius:8px;text-decoration:none;font-weight:bold;font-size:1.1em;">💬 Join Discord — Get Early Access</a>
</div>

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
