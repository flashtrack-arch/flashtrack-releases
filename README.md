<p align="center">
  <img src="assets/logo.png" alt="FlashTrack logo" width="160">
</p>

<h1 align="center">FlashTrack</h1>

<p align="center">
  An overlay for <b>League of Legends</b> that shows when each enemy's <b>Flash</b>, and their other summoner spells, will be back up.
</p>

<p align="center">
  <a href="https://github.com/flashtrack-arch/flashtrack-releases/releases/latest/download/FlashTrack-win-x64.zip"><b>Download for Windows</b></a>
  ·
  <a href="https://github.com/flashtrack-arch/flashtrack-releases/releases/latest/download/FlashTrack-osx-arm64.zip"><b>Download for macOS</b></a>
  ·
  <a href="https://github.com/flashtrack-arch/flashtrack-releases/releases">All versions</a>
</p>

You see an enemy Flash, you open the scoreboard and click their Flash icon: a countdown appears over the game, already corrected for their summoner spell haste (Ionian Boots, Crimson Lucidity, Cosmic Insight). No more "flash 12:30" in chat that nobody reads.

## Features

- Detects game start and end, your team and the five enemies on its own.
- Tracks Flash and every other summoner spell (Teleport, Ghost, Heal, Exhaust, Cleanse, Barrier, Ignite), plus the top laner's bonus Teleport from the role quest. Smite is ignored.
- Cooldowns computed from the enemy's items and runes; based on the game clock, so pauses do not skew them.
- Transparent overlay: only the enemies with a running timer are shown, and only while the game is in front.
- Works at every common resolution: nothing to calibrate.
- Starts with your computer and sleeps until League of Legends opens.
- Speaks your computer's language: English, French, Spanish, German, Korean, simplified and traditional Chinese, Vietnamese, European and Brazilian Portuguese, Turkish and Polish; English otherwise.

## Requirements

- Windows 10 or 11, or macOS 13 or later on Apple Silicon.
- League of Legends in **Borderless** window mode (nothing can be drawn over exclusive fullscreen).

## Installation

### Windows

1. [Download `FlashTrack-win-x64.zip`](https://github.com/flashtrack-arch/flashtrack-releases/releases/latest/download/FlashTrack-win-x64.zip), unzip it anywhere and launch `FlashTrack.exe`.
2. FlashTrack is not code-signed: your browser may say the file is not commonly downloaded, and on the first launch Windows shows "Windows protected your PC". Click *More info* › *Run anyway*.
3. A small bar appears at the top left and an icon next to the clock. FlashTrack now starts with Windows; to stop that, disable it in the Task Manager's **Startup** tab.

**Update**: quit FlashTrack from the tray icon, download the new zip and replace the exe. Your settings are kept.

**Uninstall**: quit FlashTrack from the tray icon, delete the exe and the `%LocalAppData%\FlashTrack` folder, then remove the startup entry:

```bat
reg delete HKCU\Software\Microsoft\Windows\CurrentVersion\Run /v FlashTrack /f
```

### macOS

1. [Download `FlashTrack-osx-arm64.zip`](https://github.com/flashtrack-arch/flashtrack-releases/releases/latest/download/FlashTrack-osx-arm64.zip), unzip it and move `FlashTrack.app` to Applications.
2. FlashTrack is not notarized by Apple, so macOS refuses to open it the first time. Close the warning, then open *System Settings › Privacy & Security* and click *Open Anyway* next to FlashTrack (on macOS 13 and 14, right-click the app › *Open* instead). Or run, once:

   ```bash
   xattr -d com.apple.quarantine /Applications/FlashTrack.app
   ```

3. The FlashTrack icon appears in the menu bar. FlashTrack now starts at login; turn it off in *System Settings › General › Login Items*. No permission is requested.

**Update**: quit FlashTrack from the menu bar icon, download the new zip and replace the app in Applications. Your settings are kept.

**Uninstall**: quit FlashTrack from the menu bar icon, delete `FlashTrack.app` and the `~/Library/Application Support/FlashTrack` folder, then remove the login entry:

```bash
rm ~/Library/LaunchAgents/com.flashtrack.app.plist
```

The Mac version is newer and has only been tried in the Practice Tool so far: please report anything odd.

## Usage

- **Start a timer**: open the scoreboard (your scoreboard key, read from the game settings) and click the enemy's spell icon.
- **Adjust a timer**: with the scoreboard open, scroll over a countdown: ±5 seconds per notch.
- **Move or resize the overlay**: with the scoreboard open, hover it, then drag it to move it or pull a corner dot to resize it; the padlock on the top edge locks both.
- **Language**: the flag left of the bar's « – » opens the language menu. *Automatic* follows the computer's language; any other line keeps that language from then on.
- **Tray / menu bar icon**: show or hide the bar, quit.

## What FlashTrack does not do

FlashTrack does not read game memory, does not inject anything into the game, does not modify any game file and does not automate any action. It only observes where your clicks on the scoreboard land; the game still receives them. It never sends a key press to the game.

It talks to two places only: the game's own Live Client Data API, on your computer, and Riot's Data Dragon for the champion portraits. No account, no telemetry, no ads.

## Bug reports

Open an [issue](https://github.com/flashtrack-arch/flashtrack-releases/issues) and attach the two files from `%LocalAppData%\FlashTrack` on Windows or `~/Library/Application Support/FlashTrack` on macOS: `launch.log`, a short trace of each run (the language chosen, game start and end, scoreboard clicks and where they landed), and `crash.log`, should the app ever stop.

## Legal

FlashTrack is a free, unofficial tool, provided as is, without warranty. This repository only hosts the downloads; the source code is not public.

FlashTrack isn't endorsed by Riot Games and doesn't reflect the views or opinions of Riot Games or anyone officially involved in producing or managing Riot Games properties. Riot Games, and all associated properties are trademarks or registered trademarks of Riot Games, Inc.
