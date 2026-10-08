# DamnationX
<p align="center">
  <img width="512" height="768"  alt="image" src="https://github.com/user-attachments/assets/64de5c9a-e64f-4c9c-8c89-ede3522c0b18" />
</p>

DamnationX is a build of [DevilutionX](https://github.com/diasurgical/devilutionX), the open source port of Diablo. It adds optional HD art drawn with WebGPU, a lobby for playing online, and sound packs you can import from your own copy of Diablo II or Diablo II: Resurrected.

This repository only hosts the release builds. Download them from the [Releases](https://github.com/trygentic/damnationx/releases) page.

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

## Windows and Linux

There are no Windows or Linux builds yet.

## Diablo II sounds

DamnationX can replace Diablo's sounds with the ones from Diablo II or Diablo II: Resurrected, if you own either game.

- On macOS, open Settings > Audio and choose a Sound Pack. The game looks for the install, including inside CrossOver and Whisky bottles, and imports the sounds. If it can't find it, set its folder as `Diablo II Path` or `Diablo II Resurrected Path` under `[Audio]` in `diablo.ini`.
- In the browser, choose a Sound Pack in Settings > Audio, then pick the game folder in the dialog that opens. Use Chrome or Edge for Diablo II: Resurrected. Only the sounds are saved, in your browser.

Nothing from Diablo II is uploaded anywhere.

## Reporting problems

Open an issue on this repository. Say which build you used (macOS or browser), what you did, and what happened.

## License

DamnationX is based on DevilutionX and is distributed under the [Sustainable Use License](LICENSE.md). Diablo is a trademark of Blizzard Entertainment. This project is not affiliated with or endorsed by Blizzard.
