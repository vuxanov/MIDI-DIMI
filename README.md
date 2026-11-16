# MIDI DIMI

MIDI DIMI is an eight-track browser groovebox for making techno and ambient loops. It has built-in drums, synths, effects, and a step sequencer. Play on screen or connect a Novation Launch Control XL over USB.

## Play

1. Open [MIDI DIMI](https://vuxanov.github.io/MIDI-DIMI/). Select **Techno**, **Hypnotic**, or **Ambient** under **Presets**, or start with **Blank**.
2. Click **Play**. Select a track and click its grid slots to add or remove hits.
3. Turn on **Keys** to play the selected instrument. Turn on **Record** to add what you play to the loop.

## Launch Control XL

Use a desktop browser with Web MIDI support, such as Chrome. Plug in the controller, click **Connect MIDI**, and allow access. Select Factory template 1 on the MK1 or MK2, or use the DAW port on the XL 3.

The upper row selects tracks. The lower row toggles eight steps at a time or plays notes in Keys mode. Track arrows move through step groups or change octaves. Faders set track levels. Send Select or Page buttons cycle through **Mix**, **Sound**, **Mod**, and **Env** for effects, modulation, and envelopes.

## Run locally

Open `index.html` in your browser. If your browser blocks MIDI for local files, serve the folder with `python3 -m http.server 8765 --bind 127.0.0.1` and open `http://localhost:8765`.

The app generates sound and saves the current session in your browser.
