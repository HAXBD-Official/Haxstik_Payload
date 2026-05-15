<div align="center">

```
██╗  ██╗ █████╗ ██╗  ██╗    ███████╗████████╗██╗██╗  ██╗
██║  ██║██╔══██╗╚██╗██╔╝    ██╔════╝╚══██╔══╝██║██║ ██╔╝
███████║███████║ ╚███╔╝     ███████╗   ██║   ██║█████╔╝ 
██╔══██║██╔══██║ ██╔██╗     ╚════██║   ██║   ██║██╔═██╗ 
██║  ██║██║  ██║██╔╝ ██╗    ███████║   ██║   ██║██║  ██╗
╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝   ╚══════╝   ╚═╝   ╚═╝╚═╝  ╚═╝
```

### Payload Library

**A community-driven collection of DuckyScript payloads for the HAX•STIK**  
USB HID injection & security research device

[![License: MIT](https://img.shields.io/badge/License-MIT-red.svg?style=flat-square)](LICENSE)
[![Payloads](https://img.shields.io/badge/Payloads-15-brightgreen?style=flat-square)](#test-payload-index)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-blue?style=flat-square)](CONTRIBUTING.md)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey?style=flat-square)](#folder-structure)
[![HAXBD](https://img.shields.io/badge/By-HAXBD--Official-ff003c?style=flat-square)](https://github.com/HAXBD-Official)

</div>

---

## ⚡ What is HAX•STIK?

HAX•STIK is a custom-built USB HID device. When plugged into a target computer, it appears as a standard USB keyboard and executes scripted keystrokes (payloads) automatically — no drivers, no software installation needed on the target.

**Features at a glance:**

| Feature | Description |
|---------|-------------|
| ⌨️ HID Injection | DuckyScript-compatible keystroke injection |
| 📡 WiFi Control | Built-in AP + web control panel at `192.168.4.1` |
| 🔑 Keylogger | LED timing channel — no driver needed on target |
| 📦 Loot Capture | `<<LOOT>>...<</LOOT>>` auto-save protocol via USB CDC |
| 💾 Storage | On-device payload and loot file storage |
| 🛑 Emergency Stop | Halt injection mid-run from control panel |

> **HAX•STIK OS** — the firmware powering the device — is at [HAXBD-Official/HAXSTIK_OS](https://github.com/HAXBD-Official)

---

## 📁 Folder Structure

```
Haxstik_Payload/
│
├── 📂 Test Payload/       ← HAX•STIK OS A-Z diagnostics (15 payloads)
│                            Run these first to verify your device works
│
├── 📂 Recon/              ← System info gathering — read-only, safe
│                            WiFi scans, sysinfo, user enumeration
│
├── 📂 Windows/            ← Windows-specific payloads
│                            PowerShell, CMD, Registry, scheduled tasks
│
├── 📂 Linux/              ← Linux / Ubuntu payloads
│                            Bash, terminal automation
│
├── 📂 MacOS/              ← macOS payloads
│                            Terminal, AppleScript, Spotlight
│
├── 📂 Fun/                ← Harmless demos, Easter eggs, pranks
│                            Rickroll, ASCII art, typing demos
│
├── 📂 CTF/                ← Capture-the-flag helpers
│                            Automation for CTF challenges
│
└── 📂 Tools/              ← Productivity & automation
                             Clipboard tools, file ops, shortcuts
```

| Folder | Purpose | Safety |
|--------|---------|--------|
| `Test Payload/` | Verify HAX•STIK hardware + OS | ✅ Safe |
| `Recon/` | Authorized system info gathering | ✅ Safe |
| `Windows/` | Windows automation & testing | ⚠️ Varies |
| `Linux/` | Linux terminal payloads | ⚠️ Varies |
| `MacOS/` | macOS payloads | ⚠️ Varies |
| `Fun/` | Non-destructive demos | ✅ Safe |
| `CTF/` | CTF competition automation | ✅ CTF context |
| `Tools/` | Productivity helpers | ✅ Safe |

---

## 🚀 Quick Start

```
1. Plug HAX•STIK into target PC
2. Connect your phone/laptop to HAX•STIK WiFi
3. Open browser → 192.168.4.1
4. Go to Payload Manager tab
5. Upload a .txt payload from this repo
6. Press RUN
```

> The target PC sees HAX•STIK as a USB keyboard — no setup required on target.

---

## 📋 DuckyScript Command Reference

HAX•STIK uses a DuckyScript-compatible syntax:

| Command | Example | Description |
|---------|---------|-------------|
| `STRING` | `STRING hello world` | Types text as keystrokes |
| `ENTER` | `ENTER` | Presses Enter |
| `DELAY` | `DELAY 500` | Wait N milliseconds |
| `DEFAULTDELAY` | `DEFAULTDELAY 100` | Delay between every command |
| `REM` | `REM comment here` | Comment — skipped during run |
| `REPEAT` | `REPEAT 5` | Repeat previous command N times |
| `GUI` | `GUI r` | Windows key + key |
| `CTRL` | `CTRL c` | Control + key |
| `SHIFT` | `SHIFT TAB` | Shift + key |
| `ALT` | `ALT F4` | Alt + key |
| `ESCAPE` | `ESCAPE` | Escape key |
| `TAB` / `BACKSPACE` | `TAB` | Tab / Backspace |
| `HOME` / `END` | `HOME` | Home / End |
| `UPARROW` / `DOWNARROW` | `UPARROW` | Arrow keys |
| `LEFTARROW` / `RIGHTARROW` | `LEFTARROW` | Arrow keys |
| `CAPSLOCK` / `NUMLOCK` | `CAPSLOCK` | Lock key toggle |
| `F1` – `F12` | `F5` | Function keys |
| `PAGEUP` / `PAGEDOWN` | `PAGEUP` | Page navigation |
| `DELETE` | `DELETE` | Delete key |

---

## 🧩 Payload File Template

Every submitted payload **must** use this header format:

```
REM ================================================================
REM  PAYLOAD  : [Number] - [Short Name]
REM  VERSION  : 1.0
REM  AUTHOR   : [Your GitHub username]
REM  TARGET OS: [Windows / Linux / MacOS / Any]
REM  SAFE     : [YES / NO — brief reason]
REM ----------------------------------------------------------------
REM  PURPOSE:
REM    [What this payload does. 2-4 lines.]
REM
REM  PRE-REQUISITE:
REM    [What the operator must do before running. Write NONE if nothing.]
REM
REM  WHAT TO LOOK FOR:
REM    [How to confirm the payload worked. List expected outputs.]
REM ================================================================

DEFAULTDELAY 150

REM --- Payload starts here ---
```

**Rules:**
- Header block is **mandatory** — no exceptions
- `SAFE: YES` → zero permanent changes to target
- `SAFE: NO` → must state exactly what is modified, authorized use only
- No payloads designed to harm, destroy data, or evade detection on unauthorized systems
- File naming: `NN_short_description.txt` — e.g. `16_clipboard_dump.txt`

---

## 🤝 How to Contribute

1. **Fork** this repository
2. Write your payload using the template above
3. Place it in the correct category folder
4. Open a **Pull Request** with title: `Add: [payload name]`

**Before submitting, confirm:**
- [ ] Header block complete — all fields filled
- [ ] File is in the correct folder
- [ ] File name follows `NN_short_description.txt` format
- [ ] Tested on real hardware or emulator
- [ ] Output matches the `WHAT TO LOOK FOR` section
- [ ] No destructive or unauthorized-use commands

---

## 🗂️ Test Payload Index

15 official HAX•STIK OS diagnostic payloads — run in order to verify every feature:

| # | Payload | What It Tests |
|---|---------|--------------|
| 01 | `basic_ping_test` | HID alive — Notepad opens and types |
| 02 | `injection_speed_test` | 4 speed tiers: 10 / 30 / 50 / 100 ms |
| 03 | `modifier_keys_test` | SHIFT, CTRL+A, CTRL+C, CTRL+Z |
| 04 | `special_chars_test` | Symbols, brackets, common payload characters |
| 05 | `repeat_delay_commands_test` | REPEAT N and DELAY timing accuracy |
| 06 | `lock_keys_test` | CAPSLOCK and NUMLOCK toggle |
| 07 | `navigation_function_keys_test` | Arrow keys, HOME, END, TAB, F-keys |
| 08 | `gui_shortcuts_test` | GUI+R (Run), GUI+D (Desktop), GUI+E (Explorer) |
| 09 | `windows_sysinfo_safe` | hostname, whoami, ipconfig, net user — read-only |
| 10 | `wifi_scan_safe` | netsh wlan — nearby networks + saved profiles |
| 11 | `keylogger_live_test` | Known strings for keylogger channel verification |
| 12 | `loot_capture_test` | USB CDC `<<LOOT>>` marker protocol test |
| 13 | `long_string_stability_test` | 80–150 char lines — buffer overflow detection |
| 14 | `emergency_stop_test` | Slow countdown — test STOP button mid-run |
| 15 | `full_az_diagnostic` | Master run — all features tested in one payload |

---

## ⚖️ Legal & Ethics Notice

> **For authorized security research, penetration testing, CTF competitions, hardware testing, and educational use only.**

- ✅ Use only on systems you **own** or have **explicit written permission** to test
- ❌ Unauthorized use is illegal — CFAA, Computer Misuse Act, IT Act, and equivalents worldwide
- ❌ No payload may target, harm, or exfiltrate from systems without consent
- ⚠️ `SAFE: NO` payloads must only run in authorized, controlled environments
- The contributors and maintainers are **not responsible** for misuse

*By contributing or using payloads from this repository, you agree to act ethically and legally.*

---

## 📄 License

MIT — see [LICENSE](LICENSE) for details.

<div align="center">

**Built for HAX•STIK — test responsibly, hack ethically.**

[![HAXBD-Official](https://img.shields.io/badge/github-HAXBD--Official-181717?style=for-the-badge&logo=github)](https://github.com/HAXBD-Official)

</div>
