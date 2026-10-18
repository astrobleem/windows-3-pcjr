# Windows 3.0 on the IBM PCjr

320 × 200 pixels · 16 colors · PCjr shared video RAM

An experimental display driver for Windows 3.0 real mode on the IBM PCjr. Recorded Windows results are from emulators; physical PCjr hardware remains unqualified.

## Clean Setup packet: PCJRSET.ZIP

**[Download PCJRSET.ZIP →](https://raw.githubusercontent.com/astrobleem/oemdisplay-tandy/main/downloads/experimental/PCJR/PCJRSET.ZIP)** — 114,994 bytes; SHA-256 `a781614c5c8c5f6c498e6e9a82364b4c2c9c3c3f7e2b2be0c67b42b2f57c17d8`.

This current packet is a repository-file download, not a GitHub Release asset. It contains the PCjr-safe grabber, original XT Pixels fonts, static artwork, guard and launcher for clean Setup or an existing installation. The merged clean-Setup session passed in DOSBox-X; physical PCjr Setup and hardware remain unqualified. Supply your own DOS and Windows 3.0 media. See the [packet install and rollback guide](https://github.com/astrobleem/oemdisplay-tandy/blob/main/downloads/experimental/PCJR/README.MD).

## Clean-Setup route

Extract the complete `PCJREXP` folder from PCJRSET.ZIP to `C:\\PCJREXP`, run `C:\\PCJREXP\\JRGUARD` from plain DOS and continue only after **OK**. Follow the included `INSTALL.TXT` through Windows Setup; start each session with `C:\\PCJREXP\\JRWIN`. Undo through Windows Setup to restore the previous display. The [packet guide](https://github.com/astrobleem/oemdisplay-tandy/blob/main/downloads/experimental/PCJR/README.MD) has full recovery details.

## Earlier cloned-install release packet

[Download PCJR.ZIP](https://github.com/astrobleem/oemdisplay-tandy/releases/download/experimental-displays-2026-10-12/PCJR.ZIP)

Ready-built **TNDYJR.DRV**, **JRWIN.COM**, **JRGUARD.COM**, installation/rollback instructions, checksums and component notices. Bring your own Windows 3.0 installation.

**Start through `C:\PCJREXP\JRWIN` before every Windows session.** JRWIN calls JRGUARD before the existing WIN.COM /R. JRGUARD checks an existing video-memory reservation; **it does not reserve RAM**. Never bypass a refusal or use the Tandy RESERVE helper.

[Release notes](https://github.com/astrobleem/oemdisplay-tandy/releases/tag/experimental-displays-2026-10-12) · [Prerequisites](#prerequisites) · [Install](#install-in-a-clone) · [Rollback](#rollback-from-plain-dos) · [Source & support](#source--support)

[![DOSBox-X PCjr capture of the clean Windows 3.0 install, Program Manager and Main group at 320×200](https://raw.githubusercontent.com/astrobleem/oemdisplay-tandy/613137d0029817b42e141a11685182d867da911d/docs/pcjr/INSTALL/DESKTOP.PNG)](https://github.com/astrobleem/oemdisplay-tandy/blob/613137d0029817b42e141a11685182d867da911d/docs/pcjr/INSTALL/DESKTOP.PNG)

DOSBox-X `machine=pcjr`, Windows 3.0 clean-Setup capture. PR #138 merged at [613137d](https://github.com/astrobleem/oemdisplay-tandy/commit/613137d0029817b42e141a11685182d867da911d) after 40 host tests; the [session record](https://github.com/astrobleem/oemdisplay-tandy/blob/613137d0029817b42e141a11685182d867da911d/docs/pcjr/INSTALL/SESSION.JSN) reports 26/26 checks and records test source commit [9ae4408](https://github.com/astrobleem/oemdisplay-tandy/commit/9ae44084127fe5d2f0c57ee1e1842d1ee1885573). Emulator evidence only, not a hardware photo.

[![DOSBox-X PCjr emulator capture: Windows 3.0 Solitaire, with a saved window partly off screen](https://raw.githubusercontent.com/astrobleem/oemdisplay-tandy/ba980d4ccf9092c38ea22b006373f420d0f059e2/docs/pcjr/WINJR02.PNG)](https://github.com/astrobleem/oemdisplay-tandy/blob/ba980d4ccf9092c38ea22b006373f420d0f059e2/docs/pcjr/WINJR02.PNG)

DOSBox-X PCjr emulator capture: Solitaire in 16 colors. Original 640×400 capture of the 320×200 guest mode. Saved AT/EGA window positions can sit partly off screen. [Capture details and historical evidence](https://github.com/astrobleem/oemdisplay-tandy/blob/ba980d4ccf9092c38ea22b006373f420d0f059e2/docs/PCJR.MD).

### Prerequisites

- IBM PCjr with expanded conventional memory and a **32 KB video page already excluded from program allocations**. The guard accepts segments 1800h–1FFFh wholly above the DOS arena or held inside one DOS-owned system MCB (owner 0008h). Program, TSR or COMMAND.COM ownership is refused. Real PCjr expansion/reservation schemes remain unqualified; do not widen the guard to make one pass.
- A bootable backup or disposable clone of an existing Windows 3.0 installation, with a plain-DOS recovery route.
- The first launcher release requires the exact `C:\PCJREXP` and `C:\WINDOWS` paths. Keep JRWIN and JRGUARD together with the complete packet.
- Retain the existing fonts/grabber for the recorded clone route. Historical rendering tests used an AT/EGA install; the newer launcher test used EGA fonts and CGA.GR2. Fresh CGA-class installation with the older PCJR.ZIP route is unqualified. The separate PCJRSET.ZIP packet passed a clean-Setup run in DOSBox-X; physical Setup remains unqualified.
- Use a nonanimated WIN.COM. Tandy palette animation uses the wrong data port for PCjr.

Read README.TXT in the ZIP and the [updated installation/recovery guide](https://github.com/astrobleem/oemdisplay-tandy/blob/a9d341d13bc24072c0f870f8ec3fe4caee12c45a/experiments/DISPLAY3/PCJR.TXT) before changing files. The updated guide also clarifies startup-logo behavior. PCjr has no 640×200×16 mode; this packet includes no TXT40 or TGA-II driver.

### Install in a clone

1. Exit Windows completely. Extract **all** ZIP files into a new `C:\PCJREXP`, verify `SHA256.SUM` on a modern host, and back up the complete installation/image.
2. From plain DOS, save SYSTEM.INI:

   ```dos
   COPY C:\WINDOWS\SYSTEM.INI C:\PCJREXP\SYSBACK.INI
   ```

   Stop if SYSBACK.INI already exists. Record the old `display.drv` setting and preserve any existing `C:\WINDOWS\SYSTEM\TNDYJR.DRV` separately.
3. Copy the driver:

   ```dos
   COPY C:\PCJREXP\TNDYJR.DRV C:\WINDOWS\SYSTEM\TNDYJR.DRV
   ```

4. With a DOS editor, change only `[boot]` → `display.drv` in SYSTEM.INI to `display.drv=TNDYJR.DRV`. Retain the font/grabber configuration.
5. Start Windows **only** with:

   ```dos
   C:\PCJREXP\JRWIN
   ```

Repeat that command after every exit. Every invocation runs JRGUARD again; a refusal prevents Windows from starting. Do not relocate part of the package or use an unguarded shortcut. A successful normal exit returns to DOS in `C:\WINDOWS`.

### Rollback from plain DOS

Exit Windows completely, or reboot to DOS if Windows will not start. Restore the saved configuration:

```dos
COPY C:\PCJREXP\SYSBACK.INI C:\WINDOWS\SYSTEM.INI
```

Restore any pre-existing TNDYJR.DRV you replaced. Restore the complete backup if other settings changed. Only after restoring the original display configuration may its original startup route be used.

### Recorded results and limits

The exact driver booted Windows 3.0 in DOSBox-X PCjr emulation, with dialogs, Program Manager, Solitaire, exit and guarded restart. Tests used DOSBox-X internal DOS, emulated serial input and an AT keyboard setting. Saved Program Manager groups/windows can look damaged or clipped when reused at the smaller geometry.

JRWIN passed 14 stub-Windows control cases, actual guard acceptance/refusal and two guarded Windows 3.0 start/normal-exit cycles at 320×200×16 in an owned clone. These are emulator runs of Windows, not physical-machine tests. The newer run checks display caps and normal exit, not a new full rendering oracle. [Launcher/rebuild record](https://github.com/astrobleem/oemdisplay-tandy/blob/37b504be3619032f435381eded7d92a504d8d9da/experiments/DISPLAY3/NATIVE.JSN).

**Physical PCjr, real DOS memory expansion/reservation, PCjr keyboard/mouse paths, timing, fresh Setup, DOS-box/grabber switching and full Paintbrush save/reopen/ROP/frame-oracle coverage remain unqualified.**

[![DOSBox-X PCjr emulator capture: Program Manager redrawn after Solitaire closes](https://raw.githubusercontent.com/astrobleem/oemdisplay-tandy/ba980d4ccf9092c38ea22b006373f420d0f059e2/docs/pcjr/WINJR03.PNG)](https://github.com/astrobleem/oemdisplay-tandy/blob/ba980d4ccf9092c38ea22b006373f420d0f059e2/docs/pcjr/WINJR03.PNG)

DOSBox-X PCjr emulator capture: Program Manager after closing Solitaire. Original capture, including the clipped saved window position; not a physical-hardware photo.

### Startup logo

The packet supplies no splash/logo, runs no Setup and does not rebuild WIN.COM. JRWIN retains the existing WIN.COM and calls it with `/R` after the mandatory guard. A compatible stock loader can show Microsoft's original static logo; a customized loader can show other art or no image. The Tandy wave is not invoked, and there is no automatic logo fallback. Logo appearance/compatibility on PCjr has not been separately qualified.

### Source & support

This repository is the documentation and download front door. All implementation, builds, fixes, canonical releases and issue tracking live in [astrobleem/oemdisplay-tandy](https://github.com/astrobleem/oemdisplay-tandy).

- [Report a problem or request a change](https://github.com/astrobleem/oemdisplay-tandy/issues)
- [Matching adaptation/build/test source — DISP3SRC.ZIP](https://github.com/astrobleem/oemdisplay-tandy/releases/download/experimental-displays-2026-10-12/DISP3SRC.ZIP)
- [Release qualification — QUALIFY.JSON](https://github.com/astrobleem/oemdisplay-tandy/releases/download/experimental-displays-2026-10-12/QUALIFY.JSON)
- [Published SHA-256 checksums](https://github.com/astrobleem/oemdisplay-tandy/releases/download/experimental-displays-2026-10-12/SHA256SUMS)

Release/package source: [`37b504be3619032f435381eded7d92a504d8d9da`](https://github.com/astrobleem/oemdisplay-tandy/commit/37b504be3619032f435381eded7d92a504d8d9da). Runtime adaptation and screenshot evidence: [`ba980d4ccf9092c38ea22b006373f420d0f059e2`](https://github.com/astrobleem/oemdisplay-tandy/commit/ba980d4ccf9092c38ea22b006373f420d0f059e2).
PR #138's clean-install evidence was merged at [613137d](https://github.com/astrobleem/oemdisplay-tandy/commit/613137d0029817b42e141a11685182d867da911d). It did not publish a new `PCJR.ZIP`; the downloadable asset above remains from the [2026-10-12 release commit](https://github.com/astrobleem/oemdisplay-tandy/commit/37b504be3619032f435381eded7d92a504d8d9da).

`PCJR.ZIP` SHA-256: `e2f471329f03c518faf6dee9ad019b2cfb56b14305c7c7a81170d04b30162aa9`.

Component notices/license scope are in NOTICE.TXT and LICENSE.TXT; the derived driver is not blanket MIT-licensed. Windows, DOS, fonts/grabbers, ROMs, compilers and original DDK inputs are not included. Do not share installation images or backups containing Windows/DOS files.
