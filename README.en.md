> 🌐 **Language / 语言**：**English** · [中文](README.md)

# 🛡️ SAC Anti-Cheat — Host-Side Anti-Cheat for Multiplayer

> 🎮 **SAC (Sentinel Anti-Cheat)** is a **host-side anti-cheat plugin** for **Casualties Unknown** (multiplayer mod `KrokoshaCasualtiesMP`), used to detect and handle cheating on the host's side.
>
> 🧩 **Version**: `1.2.101` · **Plugin file**: `SAC.dll` · **Platform**: BepInEx 5 / .NET 4.8
>
> 👤 **Author**: 小狐狸 (Little Fox) — developed and maintained

---

## 📖 Table of Contents

- [✨ Overview](#-overview)
- [🎯 What It Can Detect](#-what-it-can-detect)
- [🚀 Install & Usage](#-install--usage)
- [🗂️ Data Folder](#️-data-folder)
- [🖼️ UI Overview](#️-ui-overview)
- [📅 Changelog](#-changelog)
- [⚠️ Notes & Disclaimer](#️-notes--disclaimer)

---

## ✨ Overview

SAC runs **only on the host's side**.

- **Host-only**: clients install nothing, notice nothing, and normal players are unaffected.
- **Behavioral cheats**: covers movement, combat, interaction, minigames, medical and state-related cheating.
- **Record & act**: violation scoring, evidence logging, ban list and an OP whitelist; handling is configurable (detect only / kick on threshold / revert abnormal behavior).
- **Visual**: management panel (F7) and debug monitor (F8), with switchable Chinese/English UI.
- **Centralized data**: all runtime data lives under `SAC/` for easy backup.

> Design stance: **prefer missing a cheat over falsely punishing a legit player.** Most verdicts require streak confirmation, with exemption windows for joining, map switches, teleports, etc.

---

## 🎯 What It Can Detect

> This only lists *which* cheat behaviors are recognized — not *how*.

- 🏃 **Movement**: speed / teleport / through-wall / flight / air-jump / high-jump / wall-jump spam / anti-ragdoll / fake jetpack / anti-weight
- ⚔ **Combat**: melee reach & speed / fire rate / no-recoil
- 📦 **Interaction**: through-wall & over-distance pickup/interaction; push spam / over-distance / through-wall; abnormal carry
- 🔓 **Minigames**: instant unlock / instant completion / auto keypad / auto bandage / instant amputation / instant shrapnel removal / auto generator / one-key detonation
- 🧬 **State**: item teleport, faked state, timer anomalies
- 🛰 **Identity**: cheat-mod mutual-recognition markers
- 🚫 **Not detectable**: purely client-side visual cheats (ESP / aim assist / wallhack / FullBright) leave no host-visible behavior

---

## 🚀 Install & Usage

### Requirements

- Install **BepInEx 5** (recommended `5.4.x` or newer) into the game folder.
- Have **Casualties Unknown** and the multiplayer mod **KrokoshaCasualtiesMP** installed.
- On startup the plugin **checks the local environment** (game version / mod version / BepInEx version) and shows a notice on mismatch.

### Install

1. Copy `SAC.dll` into:
   ```
   <game>\BepInEx\plugins\SAC.dll
   ```
2. Launch the game — the plugin loads automatically.
3. **Only the host needs it.** When joining a multiplayer room, make sure you are the **host**.

> ⚠️ On first launch a one-time **notice** is shown (explaining the plugin's limits). Click "I understand" to continue.

### Hotkeys

| Key | Function |
|---|---|
| `F7` | Open/close the **anti-cheat management panel** |
| `F8` | Open/close the **debug monitor** |

### Management Panel (F7)

- **Players**: online list, **OP / Kick / Ban**.
- **Violations**: violation records / suspected list / ban list.
- **Settings**: grouped parameters, UI language, window appearance; applied instantly.
- **Game Status**: FPS, memory, multiplayer status, ping, etc.
- **About**: features and environment.

### Console Commands (input box at the bottom of Settings)

```
get / set / options / kick / ban / unban / banlist / reload / save
```

---

## 🗂️ Data Folder

```
BepInEx/plugins/
├── SAC.dll                      Anti-cheat plugin
└── SAC/                         Runtime data (auto-created)
    ├── config.json              All tunable parameters
    ├── evidence-YYYYMMDD.json   Evidence records
    ├── suspected-cheaters.json  Suspected-cheater list
    ├── oplist.json              OP whitelist
    ├── packet-filter.json       Packet filter config (debug)
    └── banlist.json             Ban list
```

---

## 🖼️ UI Overview

- **Main panel (F7)**: rounded dark theme, multiple tabs (emoji + text), free resize, transition animations, adjustable opacity.
- **Debug monitor (F8)**: live player info, suspicious packets, recent log — collapsible.
- **Cheat info window**: a separate floating window for violators, not bound to a hotkey.
- **Chinese/English UI**: follows the system language on startup, switchable in Settings.

---

## 📅 Changelog

**V1.2.101 / V1.2**
- Expanded recognition across many cheat behaviors (movement / interaction / medical / state / timer, etc.).
- Added an **Intercept + Pull Back** handling mode (revert abnormal behavior), designed to avoid repeated triggering.
- Added: debug packet filter, first-launch notice, runtime environment check.
- UI overhaul: Chinese/English, emoji, grouped settings, sliders apply on release.
- Reworked the publish-DLL protection pipeline (anti-decompile / anti-copy) and continued stability/compatibility fixes.

**V1.0**
- First release: host-side behavioral detection, evidence logging, ban/OP lists, game status page.

---

## ⚠️ Notes & Disclaimer

- **Anti-cheat is not magic**: purely client-side visual cheats (ESP, aim assist, wallhack, FullBright, etc.) leave no host-visible behavior and cannot be detected host-side; some client-resolved features can only be inferred indirectly; false positives / misses are possible — judge by evidence and act carefully.
- **Solo-developed** (小狐狸); updates and fixes may be slow — thanks for your understanding.
- **Compatibility**: the plugin modifies game logic and may **conflict** with other BepInEx plugins / multiplayer mods (especially ones that also change movement/network logic). If something breaks, disable other plugins one by one.
- Feedback on false positives or misses is welcome.
