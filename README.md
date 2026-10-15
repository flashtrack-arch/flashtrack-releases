<p align="center">
  <img src="docs/logo.png" alt="FlashTrack logo" width="160">
</p>

# FlashTrack

An overlay for **League of Legends** that shows when each enemy's **Flash**, and their other summoner spells, will be back up.

You see an enemy Flash, you open the scoreboard and click their Flash icon: a countdown appears over the game, already corrected for their summoner spell haste (Ionian Boots, Crimson Lucidity, Cosmic Insight). No more "flash 12:30" in chat that nobody reads.

FlashTrack does not read game memory, does not inject anything and does not automate any action. It only observes your clicks on the scoreboard; the game still receives them.

## Features

- Detects game start and end, your team and the five enemies on its own.
- Tracks Flash and every other summoner spell (Teleport, Ghost, Heal, Exhaust, Cleanse, Barrier, Ignite), plus the top laner's bonus Teleport from the role quest. Smite is ignored.
- Cooldowns computed from the enemy's items and runes; based on the game clock, so pauses do not skew them.
- Transparent overlay: only the enemies with a running timer are shown, and only while the game is in front.
- Scoreboard click zones shipped for each resolution: nothing to calibrate.
- Starts with your computer and sleeps until League of Legends opens.
- Speaks your computer's language: English, French, Spanish, German, Korean, simplified and traditional Chinese, Vietnamese, European and Brazilian Portuguese, Turkish and Polish; English otherwise. The flag in the idle bar picks another one at once.

## Requirements

- Windows 10 or 11, or macOS 13 or later on Apple Silicon.
- League of Legends in **Borderless** window mode (nothing can be drawn over exclusive fullscreen).

## Installation

### Windows

1. Unzip `FlashTrack-vX.Y.Z-win-x64.zip` anywhere and launch `FlashTrack.exe`.
2. The exe is not code-signed: on the first launch, click *More info* › *Run anyway* on the "Windows protected your PC" screen.
3. A small bar appears at the top left and an icon next to the clock. FlashTrack now starts with Windows; to stop that, disable it in the Task Manager's **Startup** tab.

To update, quit FlashTrack from the tray icon and replace the exe.

### macOS

1. Unzip `FlashTrack-vX.Y.Z-osx-arm64.zip` and move `FlashTrack.app` to Applications.
2. The app is not notarized: right-click it › *Open* › *Open* the first time, or run:

   ```bash
   xattr -d com.apple.quarantine /Applications/FlashTrack.app
   ```

3. The FlashTrack icon appears in the menu bar. FlashTrack now starts at login; turn it off in *System Settings › General › Login Items*.

No permission is requested. The macOS build has only been tried in the Practice Tool so far.

## Usage

- **Start a timer**: open the scoreboard (your scoreboard key, read from the game settings) and click the enemy's spell icon.
- **Adjust a timer**: with the scoreboard open, scroll over a countdown: ±5 seconds per notch.
- **Move or resize the overlay**: with the scoreboard open, hover it, then drag it to move it or pull a corner dot to resize it; the padlock on the top edge locks both.
- **Language**: the flag left of the bar's « – » opens the language menu. *Automatic* follows the computer's language; any other line keeps that language from then on.
- **Tray / menu bar icon**: show or hide the bar, quit.

Settings and the portrait cache live in `%LocalAppData%\FlashTrack` on Windows and `~/Library/Application Support/FlashTrack` on macOS. So do `launch.log`, a short trace of each run (the language chosen, game start and end, scoreboard clicks and where they landed), and `crash.log` should the app ever stop: attach both to a bug report.

## Development

.NET 10, WPF front on Windows, Avalonia front on macOS, shared engine underneath.

```bash
dotnet build FlashTrack.slnx
dotnet test FlashTrack.slnx
```

Architecture, cooldown tables, scoreboard measurements and release steps: see [docs/technical-notes.md](docs/technical-notes.md). macOS port status: [docs/mac-port-plan.md](docs/mac-port-plan.md).

## Legal

FlashTrack only uses Riot's Live Client Data API and Data Dragon, as allowed by Riot's third-party application policy.

FlashTrack isn't endorsed by Riot Games and doesn't reflect the views or opinions of Riot Games or anyone officially involved in producing or managing Riot Games properties. Riot Games, and all associated properties are trademarks or registered trademarks of Riot Games, Inc.

The source code is private; only the executable is meant to be distributed.
