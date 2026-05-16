# Varmojii

> **Your glyphs, on demand.**

A system-wide emoji, symbol & glyph picker for Windows, macOS, and Linux.  
Lightweight, local-first, tray-resident — always one chord away.

---

## What is Varmojii?

Varmojii replaces the broken, Windows-only `Win+.` emoji picker with a **fast, cross-platform, keyboard-summoned overlay** built for writers, developers, and worldbuilders.

Every emoji, symbol, kaomoji, phonetic character, and Unicode glyph you need — always one chord away, insertable directly into any active app on any desktop OS.

- ⚡ Zero telemetry
- ☁️ Zero cloud accounts
- 💳 Zero subscriptions — ever
- 🌐 100% offline after install

---

## App Identity

| Field | Value |
|---|---|
| **App Name** | Varmojii |
| **Repository** | `github.com/TheAlarklynZone/Varmojii` |
| **Internal unit name** | Motes (individual emoji/symbol units) |
| **Tagline** | Your glyphs, on demand. |
| **License** | Apache-2.0 |
| **Telemetry** | None |
| **Cloud/account required** | None |
| **Subscription/Pro tier** | None — ever |
| **Theme** | Dark-mode-first, follow-system option |

---

## Name Logic

- **Var** → variables, reusable values, dev/tech energy (consistent with the Quilvar ecosystem's `-var` suffix)
- **Moji** → emoji, glyphs, expressive symbols
- **Double-i** → distinct, memorable, fantasy-tech signature
- **Motes** → individual emoji/symbol units; a mote is a tiny meaningful particle — exactly what emoji are

---

## Global Shortcut

Shortcuts are **hardwired** — intentional and by design. No customization option.

| Platform | Shortcut | Implementation |
|---|---|---|
| Windows | `RCtrl + RShift + RAlt + E` | `rdev` Rust crate — raw key hook, right-side modifiers only |
| Linux | `RCtrl + RShift + RAlt + E` | `rdev` Rust crate — X11/Wayland raw input |
| macOS | `Ctrl + Shift + Option + P` | Tauri standard global hotkey registration |

The right-side modifier chord is deliberate — spacious, under-used, and feels like an intentional gesture rather than an accidental combo.

---

## Core Features

### ⚡ Quick Draw Overlay *(The Star Feature)*
The primary interaction surface — summoned by the global shortcut from anywhere on the system.

- Appears as a compact floating overlay near the cursor or screen center
- Search field focused immediately — no clicks required
- Type any emoji name, keyword, Unicode codepoint, or character description
- Results update instantly across all Mote categories
- Arrow keys to navigate, `Enter` to insert directly into the active app
- `Esc` to dismiss with no side effects
- Insert method: OS-level input injection via `enigo` — **no visible clipboard roundtrip**

### 🗂️ Mote Sets *(Named Profiles)*
Each Mote Set is a named collection of preferred/pinned Motes scoped to a context.

Example sets:
- **Writing** — em dashes, quotation marks, IPA symbols
- **Discord** — most-used emoji and kaomoji
- **Code** — math operators, arrows, Greek variables
- **Hibrythian Saga** — worldbuilding-specific symbols and glyphs

Up to 5 named sets in v1.0.0. Switch active set from the tray or main window.

### 📌 Pins & Recents
- **Recents** — last N used Motes, persists across restarts
- **Pinned Motes** — manually pinned, never auto-deleted, renameable and reorderable
- Both surfaces are fully searchable

### 🔍 Search
Search across all categories simultaneously or filter by category tab:
- Emoji/symbol name (`fire`, `copyright`, `theta`)
- Keyword/tag (`happy`, `shrug`, `math`)
- Unicode codepoint (`U+1F525`, `U+00A9`)
- Phonetic description (`schwa`, `glottal stop`, `velar nasal`)

---

## Mote Types (Content Categories)

| Category | Internal Name | Unicode Block |
|---|---|---|
| 😄 Emoji | Motes | Full Unicode emoji set |
| (◕‿◕) Kaomoji | Kaomotes | Text strings (hand-curated by Alarkius Elvya Jay) |
| ✦ Decorative Symbols | Glyphmotes | Arrows U+2190–U+21FF, Misc U+2600–U+26FF |
| © Legal & Special | Legalmotes | Letterlike Symbols U+2100–U+214F |
| ∑ Math & Science | Mathmotes | Math Operators U+2200–U+22FF |
| $ Currency | Curmotes | Currency Symbols U+20A0–U+20CF |
| α Greek | Hellenmotes | Greek & Coptic U+0370–U+03FF |
| ʃ Phonetic / IPA | Phonmotes | IPA Extensions U+0250–U+02AF |

All content is sourced from [unicode.org](https://unicode.org) public data and **bundled locally at build time**. Zero runtime network calls. Works fully offline after installation.

> **Kaomotes are hand-curated and owned by Alarkius Elvya Jay** — not scraped or licensed from a third party. Each kaomoji is tagged by mood/expression for search purposes.

---

## Tech Stack

| Layer | Technology | Reason |
|---|---|---|
| App shell | Tauri (Rust backend) | Tiny binary (~5MB), true cross-platform, native tray |
| Frontend | React 18 + Vite + Tailwind CSS | Consistent with Quillosofi stack |
| Global hotkey | `rdev` Rust crate | Only library exposing L/R modifier distinction on Win/Linux |
| Direct insert | `enigo` Rust crate | OS-level input injection, no clipboard roundtrip |
| Data | Local bundled JSON (unicode.org sourced) | 100% offline, zero runtime API calls |
| Auto-updater | `tauri-plugin-updater` via GitHub Releases | Consistent with org pipeline |
| Local persistence | `tauri-plugin-store` | Pins, recents, Mote Sets stored safely on disk |
| Build/CI | GitHub Actions on `v` tag push | Consistent with existing org pipeline |

---

## Ecosystem Fit

| App | Repo | Purpose |
|---|---|---|
| **Quillosofi** | `TheAlarklynZone/Quillosofi` | Writing and worldbuilding desktop app |
| **Quilvar** | `TheAlarklynZone/Quilvar` | Clipboard manager |
| **MultiRP** | `AlarkiusJay/MultiRPCustomizer` | Discord Rich Presence manager |
| **Varmojii** | `TheAlarklynZone/Varmojii` | System-wide glyph and emoji picker |

---

## MVP Scope (v1.0.0)

- ✅ Tray app on Windows, macOS, Linux via Tauri
- ✅ Global hotkey → Quick Draw overlay (hardwired, platform-specific)
- ✅ All eight Mote categories bundled locally
- ✅ Search-as-you-type across all categories
- ✅ Direct insert via `enigo`
- ✅ Persistent recents (survives restart)
- ✅ Pinned Motes
- ✅ Mote Sets (named profiles, up to 5)
- ✅ Dark mode default, follow-system option
- ✅ Right-click menus: tray, Motes, Sets
- ✅ In-app auto-updater via GitHub Releases
- ✅ No telemetry, no cloud, no account

---

## Post-MVP Roadmap

- **Quilvar integration** — share pinned clips between Quilvar and Varmojii
- **Custom Mote Sets export/import** — share your Writing or worldbuilding set with others
- **Skin tone presets** — per-Mote-Set default skin tone modifier for emoji
- **Symbol mode hotkey** — quick toggle to symbol-only view from Quick Draw
- **Quillosofi integration** — Varmojii Quick Draw accessible from inside Quillosofi directly
- **Additional Kaomotes** — community-submitted kaomoji additions

---

## Status

> 🚧 **Early development.** MVP in planning phase.  
> Handoff destination: [Bolt.new](https://bolt.new)

---

## Credits

Designed and created by **Alarkius Elvya Jay**  
Author, worldbuilder, and composer behind *The Hibrythian Saga* and *The Naiseikai Universe*  
Part of the [TheAlarklynZone](https://github.com/TheAlarklynZone) project suite

---

*Varmojii — every glyph you need, one chord away.*
