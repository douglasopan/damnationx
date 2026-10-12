# DamnationX
<p align="center">
  <img width="512" height="768"  alt="image" src="https://github.com/user-attachments/assets/64de5c9a-e64f-4c9c-8c89-ede3522c0b18" />
</p>

DamnationX is a build of [DevilutionX](https://github.com/diasurgical/devilutionX), the open source port of Diablo. It adds optional HD art drawn with WebGPU, a lobby for playing online, and sound packs you can import from your own copy of Diablo II or Diablo II: Resurrected.

This repository only hosts the release builds. Download them from the [Releases](https://github.com/trygentic/damnationx/releases) page.

## Latest beta

Beta 4 adds the first Windows, Linux and Android downloads. The game itself is the same as beta 3, so the macOS app and browser build from beta 3 are still current. The new builds play single player and support DevilutionX's TCP/IP and ZeroTier multiplayer, but they can't reach the DamnationX lobby yet. They don't include the WebGPU HD art renderer either.

## You need the Diablo game data

DamnationX doesn't include Diablo's art, music or sounds. You need `DIABDAT.MPQ` from a copy you own:

- Diablo from [GOG.com](https://www.gog.com/game/diablo) or Battle.net: the file is in the game folder. With the GOG installer you can also [extract it](https://github.com/diasurgical/devilutionX/wiki/Extracting-MPQs-from-the-GoG-installer).
- The original CD: the file is on the disc.
- No copy? `spawn.mpq` from the [shareware version](https://github.com/diasurgical/devilutionx-assets/releases/latest/download/spawn.mpq) lets you play the shareware part of the game.

## Play on macOS

This build needs an Apple Silicon Mac (M1 or newer) running macOS 26 or later.

1. Download `DamnationX-<version>-macos-arm64.zip` from the latest release and unzip it.
2. Move `DamnationX.app` to your Applications folder.
3. Copy `DIABDAT.MPQ` into `~/Library/Application Support/diasurgical/devilution/`. In Finder, press Cmd+Shift+G and paste that path. Create the folder if it doesn't exist.
4. The app isn't signed by Apple, so macOS blocks it the first time. Right-click `DamnationX.app`, choose Open, then confirm. If macOS still refuses, run this once in Terminal:

   ```
   xattr -dr com.apple.quarantine /Applications/DamnationX.app
   ```

5. Open the app. Single Player works offline. Multi Player connects to the lobby at `lobby.damnationx.net`.

## Play in a browser

The simplest option is the hosted version at [damnationx.net](https://damnationx.net). Click Game files…, choose your `DIABDAT.MPQ`, then click Play.

To host the browser build yourself:

1. Download `DamnationX-<version>-web.zip` and unzip it.
2. Serve the folder over HTTP. Opening `index.html` straight from disk doesn't work. With Python, for example:

   ```
   cd DamnationX-<version>-web
   python3 -m http.server 8000
   ```

3. Open `http://localhost:8000` in Chrome or Edge. WebGPU needs a secure context, and `localhost` counts as one. On another host, use HTTPS.
4. Click Game files…, choose your `DIABDAT.MPQ`, then click Play.

If you use another web server, make sure it sends `.wasm` files as `application/wasm`.

A copy you host yourself is for single player. For online games, play at [damnationx.net](https://damnationx.net) or use the macOS app.

## Play on Windows

The Windows build is for 64-bit Windows.

1. Download `DamnationX-<version>-windows-x64.zip` and unzip it anywhere.
2. Copy `DIABDAT.MPQ` into the unzipped folder, next to `devilutionx.exe`. You can also put it in `%APPDATA%\diasurgical\devilution\`.
3. Run `devilutionx.exe`. The program isn't signed, so Windows SmartScreen may warn you the first time. Click More info, then Run anyway.

## Play on Linux

There are builds for x86_64 and for 64-bit ARM (aarch64).

1. Download `DamnationX-<version>-linux-x86_64.tar.xz` or `DamnationX-<version>-linux-arm64.tar.xz` and extract it.
2. Copy `DIABDAT.MPQ` into `~/.local/share/diasurgical/devilution/`, or into the extracted folder next to `devilutionx`.
3. Run `./devilutionx`. On x86_64, run `./devilutionx.sh` instead if you want Discord status to work.

The archive also contains `devilutionx.deb` and `devilutionx.rpm` if you'd rather install it with your package manager. Either way you need SDL2, SDL2_image and libpng from your distribution. The builds were made on Ubuntu 24.04, so they need a distribution with glibc 2.39 or newer.

## Play on Android

The Android build needs Android 5.0 or later.

1. Download `DamnationX-<version>-android.apk` on the device and open it. Allow installs from your browser or file manager if Android asks.
2. Open DevilutionX (Dev). It asks for the game data the first time: pick your `DIABDAT.MPQ`, or download the shareware data.

This APK is a debug build signed with a development key. It installs next to an existing DevilutionX app rather than replacing it, and a later release signed with a different key may need you to uninstall it first. Your saves are kept in the app's folder under `Android/data/org.diasurgical.devilutionx.dev/`.

## Diablo II sounds

DamnationX can replace Diablo's sounds with the ones from Diablo II or Diablo II: Resurrected, if you own either game.

- On macOS, open Settings > Audio and choose a Sound Pack. The game looks for the install, including inside CrossOver and Whisky bottles, and imports the sounds. If it can't find it, set its folder as `Diablo II Path` or `Diablo II Resurrected Path` under `[Audio]` in `diablo.ini`.
- In the browser, choose a Sound Pack in Settings > Audio, then pick the game folder in the dialog that opens. Use Chrome or Edge for Diablo II: Resurrected. Only the sounds are saved, in your browser.

Nothing from Diablo II is uploaded anywhere.

## Reporting problems

Open an issue on this repository. Say which build you used (macOS, Windows, Linux, Android or browser), what you did, and what happened.

## License

DamnationX is based on DevilutionX and is distributed under the [Sustainable Use License](LICENSE.md). Diablo is a trademark of Blizzard Entertainment. This project is not affiliated with or endorsed by Blizzard.
