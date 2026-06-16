# CaptionsRush for OBS — Releases

Public release artifacts for the [CaptionsRush OBS plugin](https://captionsrush.com).

**Downloads:** see the [Releases](../../releases) tab.

Source code lives in a private repository. This repo only hosts signed installers
and slim ZIPs published by CI on every tagged release.

## Installation
### Windows
1. Quit OBS Studio.
2. Run `captionsrush-obs-0.10.0-windows-x64-Setup.exe`. Installs into
   `%ProgramData%\obs-studio\plugins\captionsrush-obs\` (no admin prompt — per-user).
3. Relaunch OBS.

#### Manual install from the ZIP (alternative to the installer)

If you'd rather not run the installer (corporate policy, scripted deployment,
offline media, etc.), the ZIP contains exactly the same files. The plugin DLL
inside is identically Authenticode-signed.

1. **Quit OBS Studio** before copying any files.
2. Extract `captionsrush-obs-0.10.0-windows-x64.zip`. You'll get a folder named
   `captionsrush-obs/` with this layout:
   ```
   captionsrush-obs/
     bin/
       64bit/
         captionsrush-obs.dll
         abseil_dll.dll, cares.dll, libcrypto-3-x64.dll, libcurl.dll,
         libprotobuf.dll, libssl-3-x64.dll, re2.dll, z.dll
     data/
       locale/
         en-US.ini
   ```
3. **Move the entire `captionsrush-obs\` folder** into the OBS per-user plugins
   directory:
   ```
   %ProgramData%\obs-studio\plugins\
   ```
   The final path of the DLL should be
   `%ProgramData%\obs-studio\plugins\captionsrush-obs\bin\64bit\captionsrush-obs.dll`.
   `%ProgramData%` is normally `C:\ProgramData` (a hidden system folder — paste
   the path into Explorer's address bar, don't browse to it).
4. Relaunch OBS. Confirm the plugin loaded by checking
   `%APPDATA%\obs-studio\logs\<latest>.txt` — you should see a `[CaptionsRush]`
   prefix on a few startup lines.

#### Uninstalling the manual install

Quit OBS and delete
`%ProgramData%\obs-studio\plugins\captionsrush-obs\`. Plugin settings live at
`%APPDATA%\obs-studio\plugin_config\captionsrush-obs\` if you also want to wipe
those.

#### Don't use `%APPDATA%\obs-studio\plugins\`

OBS docs list a per-user plugin path under `%APPDATA%`, but on real installs it
typically doesn't load plugins from there. Use the `%ProgramData%` path above.

### Mac (Apple Silicon only)
1. Unzip the download to get captionsrush-obs.plugin, then move it into `~/Library/Application Support/obs-studio/plugins/` (create that folder if needed).
2. Quit and relaunch OBS — the CaptionsRush dock appears under the Docks menu.

### Both (after install)
1. **View → Docks → CaptionsRush** to open the dock.
2. Sign in (Google, Discord, or email + password).
3. **Sources → +** → "CaptionsRush Captions" to add the on-canvas caption source.
4. Pick an audio source in the dock, choose a language, hit **Start**.

## System requirements

- Windows 10 1809 (build 17763) or later, 64-bit
- Mac Apple Silicon (M1 and or later)
- OBS Studio 31 or later
- A CaptionsRush account (free tier available at <https://captionsrush.com>)

## Known limitations
- In Windows, The plugin's signing certificate is recent; SmartScreen may show a
  "less common app" warning for the first few hundred downloads until
  reputation accrues. Click **More info → Run anyway**.
