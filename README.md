# HAX•STIK Payload Library

A community-driven collection of DuckyScript payloads for the **HAX•STIK** — a custom USB HID injection and security research device.

This repository is open for contribution. Anyone can submit payloads, fix bugs, or improve existing scripts. All payloads must follow the ethics and format rules below.

---

## What is HAX•STIK?

HAX•STIK is a custom-built USB HID device. When plugged into a target computer, it appears as a USB keyboard and executes scripted keystrokes (payloads) automatically.

**Key features:**
- USB HID keyboard injection (DuckyScript-compatible)
- Built-in WiFi access point + web control panel
- USB CDC serial channel for keylogger and loot capture
- `<<LOOT>>...<</LOOT>>` marker protocol for auto-saving captured data
- LED timing channel keylogger (no driver needed on target)
- SPIFFS-based payload and loot storage

**HAX•STIK OS** is the firmware that runs on the device — hosted at [HAXBD-Official/HAXSTIK_OS](https://github.com/HAXBD-Official).

---

## Folder Structure

```
Haxstik_Payload/
│
├── Test Payload/          # HAX•STIK OS A-Z diagnostic payloads
│                          # Run these to verify HAXSTIK is working correctly
│
├── Recon/                 # System info gathering (read-only, safe)
│                          # WiFi scans, sysinfo, user enumeration
│
├── Windows/               # Windows-specific payloads
│                          # PowerShell, CMD, Registry, scheduled tasks
│
├── Linux/                 # Linux / Ubuntu payloads
│                          # Bash, terminal automation
│
├── MacOS/                 # macOS payloads
│                          # Terminal, AppleScript, Spotlight
│
├── Fun/                   # Harmless demos, pranks, Easter eggs
│                          # Rickroll, ASCII art, typing demos
│
├── CTF/                   # CTF competition helpers
│                          # Automation for capture-the-flag challenges
│
└── Tools/                 # Productivity and automation payloads
                           # File ops, clipboard tools, shortcuts
```

---

## Payload Categories Explained

| Folder | Purpose | Safety Level |
|--------|---------|-------------|
| `Test Payload/` | Diagnose and verify HAX•STIK hardware + OS | Safe — read-only |
| `Recon/` | Gather system info on authorized targets | Safe — read-only |
| `Windows/` | Windows automation and testing payloads | Varies — check each file |
| `Linux/` | Linux terminal payloads | Varies — check each file |
| `MacOS/` | macOS payloads | Varies — check each file |
| `Fun/` | Harmless demos, non-destructive pranks | Safe |
| `CTF/` | CTF challenge automation | Safe in CTF context |
| `Tools/` | Productivity automation | Safe |

---

## How to Use a Payload

1. Open **HAX•STIK OS** control panel via WiFi (`192.168.4.1`)
2. Go to the **Payload Manager** tab
3. Upload a `.txt` payload file from this repo
4. Click **Run** — HAX•STIK will execute the script as a USB keyboard

**Important:** Plug HAX•STIK into the target PC before running. The target PC sees it as a standard USB keyboard — no drivers needed.

---

## DuckyScript Command Reference

HAX•STIK uses a DuckyScript-compatible syntax. Supported commands:

| Command | Example | Description |
|---------|---------|-------------|
| `STRING` | `STRING hello world` | Types a string as keystrokes |
| `ENTER` | `ENTER` | Presses Enter key |
| `DELAY` | `DELAY 500` | Waits N milliseconds |
| `DEFAULTDELAY` | `DEFAULTDELAY 100` | Sets delay between every command |
| `REM` | `REM comment` | Comment — ignored during execution |
| `REPEAT` | `REPEAT 5` | Repeats the previous command N times |
| `GUI` | `GUI r` | Windows key + key (e.g. GUI r = Run dialog) |
| `CTRL` | `CTRL c` | Control + key |
| `SHIFT` | `SHIFT TAB` | Shift + key |
| `ALT` | `ALT F4` | Alt + key |
| `ESCAPE` | `ESCAPE` | Presses Escape |
| `TAB` | `TAB` | Presses Tab |
| `BACKSPACE` | `BACKSPACE` | Presses Backspace |
| `DELETE` | `DELETE` | Presses Delete |
| `HOME` | `HOME` | Presses Home |
| `END` | `END` | Presses End |
| `UPARROW` | `UPARROW` | Up arrow key |
| `DOWNARROW` | `DOWNARROW` | Down arrow key |
| `LEFTARROW` | `LEFTARROW` | Left arrow key |
| `RIGHTARROW` | `RIGHTARROW` | Right arrow key |
| `CAPSLOCK` | `CAPSLOCK` | Toggles Caps Lock |
| `NUMLOCK` | `NUMLOCK` | Toggles Num Lock |
| `F1`–`F12` | `F5` | Function keys |
| `PAGEUP` | `PAGEUP` | Page Up |
| `PAGEDOWN` | `PAGEDOWN` | Page Down |

---

## Payload File Template

Every payload submitted to this repo **must** follow this format:

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
REM    [Anything the operator must do before running this payload.]
REM    [Write NONE if nothing is needed.]
REM
REM  WHAT TO LOOK FOR:
REM    [How to verify the payload worked correctly.]
REM    [List expected outputs or visible results.]
REM ================================================================

DEFAULTDELAY 150

REM --- Your payload starts here ---
```

**Rules:**
- Header block is mandatory — no exceptions
- `SAFE: YES` payloads must make zero permanent changes to the target
- `SAFE: NO` payloads must clearly state what they modify and require explicit authorization
- No payload may be designed to harm, destroy data, or evade detection on unauthorized targets
- File name format: `NN_short_description.txt` (e.g. `16_clipboard_dump.txt`)

---

## How to Contribute

1. **Fork** this repository
2. Create your payload file following the template above
3. Place it in the correct category folder
4. Submit a **Pull Request** with:
   - A short title: `Add: [payload name]`
   - A description of what it does and what OS it targets
   - Confirm it is tested on real hardware or emulator

**Contribution checklist:**
- [ ] Header block is complete (all fields filled)
- [ ] File is in the correct category folder
- [ ] File name follows `NN_short_description.txt` format
- [ ] Payload has been tested — results match the `WHAT TO LOOK FOR` section
- [ ] No destructive or unauthorized-use commands included

---

## Test Payload Index

These 15 payloads in `Test Payload/` are the official HAX•STIK OS diagnostic suite. Run them in order to verify every feature of your device:

| # | File | Tests |
|---|------|-------|
| 01 | basic_ping_test | HID alive — Notepad opens and types |
| 02 | injection_speed_test | 4 speed tiers: 10 / 30 / 50 / 100 ms |
| 03 | modifier_keys_test | SHIFT, CTRL+A, CTRL+C, CTRL+Z |
| 04 | special_chars_test | Symbols, brackets, common payload characters |
| 05 | repeat_delay_commands_test | REPEAT N and DELAY timing accuracy |
| 06 | lock_keys_test | CAPSLOCK and NUMLOCK toggle |
| 07 | navigation_function_keys_test | Arrow keys, HOME, END, TAB, F-keys |
| 08 | gui_shortcuts_test | GUI+R (Run), GUI+D (Desktop), GUI+E (Explorer) |
| 09 | windows_sysinfo_safe | hostname, whoami, ipconfig, net user (read-only) |
| 10 | wifi_scan_safe | netsh wlan — nearby networks + saved profiles |
| 11 | keylogger_live_test | Known strings for keylogger channel verification |
| 12 | loot_capture_test | USB CDC `<<LOOT>>` marker protocol test |
| 13 | long_string_stability_test | 80–150 char lines — buffer overflow check |
| 14 | emergency_stop_test | Slow countdown — test STOP button mid-run |
| 15 | full_az_diagnostic | Master A-Z run — all features in one payload |

---

## Legal & Ethics Notice

> **This repository is for authorized security research, penetration testing, CTF competitions, hardware testing, and educational purposes only.**

- Only use HAX•STIK and these payloads on systems you own or have **explicit written permission** to test
- Unauthorized use against systems you do not own is illegal in most countries (CFAA, Computer Misuse Act, IT Act, etc.)
- The contributors and maintainers of this repository are not responsible for misuse
- Payloads marked `SAFE: YES` are read-only — they gather information but make no changes
- Payloads marked `SAFE: NO` must only be used in authorized, controlled environments

By using or contributing to this repository, you agree to use these payloads **ethically and legally**.

---

## License

MIT License — see [LICENSE](LICENSE) for details.

Contributions are welcome. Be responsible. Test ethically.
