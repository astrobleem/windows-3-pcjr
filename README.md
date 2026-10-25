# Windows 3.0 on the IBM PCjr

**[Download JRPAN.ZIP](https://github.com/astrobleem/oemdisplay-tandy/releases/download/windows-xt/JRPAN.ZIP)**

The one packet includes fixed 320x200 and software-panning 320x400 displays,
fonts, PCjr grabber, logos and guarded launchers. Use installed Windows 3.0
real mode in `C:\WINDOWS`, 640 KB and a PCjr memory configuration that already
reserves the 32 KB video page. JRGUARD checks that reservation; it does not reserve RAM.

## Install

1. Extract its `JRPAN` folder to `C:\JRPAN`. Exit Windows to DOS.
2. Run `C:\JRPAN\INSTALL`. In Setup choose Display / Other, enter `C:\JRPAN`,
   and choose fixed 320x200 or software-panning 320x400. Complete changes and return to DOS.
3. Start Windows with `C:\JRPAN\JRSTART` every time so its guard runs.
4. For panning, run `C:\JRPAN\PANCFG` inside Windows once. Alt+PgDn/Alt+PgUp
   pan; Alt+F9 returns to the top. `PANCFG OFF` disables the helper before switching to fixed mode.

The panning desktop uses 32,000 additional shadow bytes. Physical PCjr memory
expansion, keyboard and timing remain unqualified; Windows 3.1 is unsupported.
Finish a DOS program using PCjr graphics to return to Windows.
[Install details](https://github.com/astrobleem/oemdisplay-tandy/blob/main/docs/SOFTPAN/RELEASE.MD).

![PCjr clean Windows 3.0 Setup in DOSBox-X](https://raw.githubusercontent.com/astrobleem/oemdisplay-tandy/main/docs/pcjr/INSTALL/DESKTOP.PNG)

[Get help](https://github.com/astrobleem/oemdisplay-tandy/issues). Component notices are in the packet.
