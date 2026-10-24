# Windows 3.0 on the IBM PCjr

**320x200, 16 colors. [Download PCJRSET.ZIP](https://raw.githubusercontent.com/astrobleem/oemdisplay-tandy/main/downloads/experimental/PCJR/PCJRSET.ZIP)**

The current packet includes the display driver, PCjr-safe grabber, XT Pixels
fonts, static startup logo, guard and launcher. It supports fresh Windows 3.0
Setup and changing an existing installation. Supply your own DOS and Windows
3.0 media, an expanded PCjr and a hard disk as C:.

The **32 KB video page at segments 1800h-1FFFh must already be excluded from
DOS allocations** by your memory configuration. JRGUARD checks that reservation;
it does not reserve RAM. Keep the fixed `C:\PCJREXP` and `C:\WINDOWS` paths.

## Install

1. Extract the complete `PCJREXP` folder to `C:\PCJREXP`.
2. From plain DOS, run `C:\PCJREXP\JRGUARD`. Continue only after **OK**.
3. Run your Windows 3.0 `SETUP`. For an existing installation, use SETUP in
   `C:\WINDOWS`; for a new installation, run it from your Windows media.
   Keep `C:\WINDOWS`, choose **Display / Other**, enter `C:\PCJREXP`, and select
   **EXPERIMENTAL IBM PCjr 320x200 16 colors**. Use **PC/XT 84-key keyboard**
   and your appropriate mouse setting. At the end, choose **Return to DOS**
   so the guard runs on the next launch.
4. Start Windows this way every time, including after reboot:

   ```bat
   C:\PCJREXP\JRWIN
   ```

JRWIN runs JRGUARD before `WIN.COM /R` and refuses to start after a failed check.
Do not bypass a refusal or substitute the Tandy RESERVE helper. For media
staging and narrow Setup dialogs, follow the included `INSTALL.TXT` or the
[full Setup guide](https://github.com/astrobleem/oemdisplay-tandy/blob/main/src/pcjr/INSTALL/INSTALL.TXT).

## Known limits and removal

Fresh and existing-install Setup passed in DOSBox-X; physical PCjr memory
expansion, keyboard, serial input and timing remain unqualified. Wide dialogs
can clip at 320 pixels. Finish DOS programs using PCjr modes 8, 9 or 0Ah to
return to Windows; Alt+Tab cannot switch away from those modes.
Windows 3.1 is not supported.

To change back, exit Windows, run JRGUARD successfully and use Windows Setup
to restore your previous display.

![PCjr clean Windows 3.0 Setup in DOSBox-X](https://raw.githubusercontent.com/astrobleem/oemdisplay-tandy/main/docs/pcjr/INSTALL/DESKTOP.PNG)

<details>
<summary>History, source and optional test records</summary>

The older [PCJR.ZIP release](https://github.com/astrobleem/oemdisplay-tandy/releases/tag/experimental-displays-2026-10-12)
was a driver-only update for an existing installation: it did not include
Setup support or a logo. Those limits describe that historical packet.
Use PCJRSET above for current installation.

[Machine and test record](https://github.com/astrobleem/oemdisplay-tandy/blob/main/docs/PCJR.MD) ·
[Packet details and checksums](https://github.com/astrobleem/oemdisplay-tandy/blob/main/downloads/experimental/PCJR/README.MD) ·
[Source and issue tracking](https://github.com/astrobleem/oemdisplay-tandy).
Component notices are included in the packet.

</details>
