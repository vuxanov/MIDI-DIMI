# MIDI DIMI

MIDI DIMI is an eight-track browser groovebox by [Dimitar Vuksanov](https://github.com/vuxanov) for making techno and ambient loops. It has built-in drums, synths, effects, and a step sequencer. Play on screen or connect a Novation Launch Control XL over USB.

## Play

1. Open [MIDI DIMI](https://vuxanov.github.io/MIDI-DIMI/). The app starts with a blank song or restores your last session.
2. Click **Play**. Select a track and click its grid slots to add or remove hits.
3. Turn on **Keys** to play the selected instrument. Turn on **Record** to add what you play to the loop.

Use **Record Audio** and **Stop Audio** to download your live mix as a stereo WAV.

## Projects and undo

Open **⋯** for **Save project** and **Open project**. Projects download as `.dimi.json` files containing all eight tracks, patterns, sounds, effects, note lengths, octaves, and BPM. Open restores the song and stops playback. The previous song can be recovered with Undo. Audio recordings remain separate WAV files; MIDI device connections and the color theme are not stored in a project.

**Undo** and **Redo** appear below the theme option. Use Cmd/Ctrl+Z for Undo, Cmd+Shift+Z on Mac or Ctrl+Y / Ctrl+Shift+Z for Redo. The latest 100 song edits are kept until you reload. Continuous knob adjustments are grouped together.

## Texture samples

Use the small arrow beside **Texture** to choose **Load sample…**, then select an audio file supported by your browser (for example WAV or MP3). Files must be under 8 MB and five minutes. The file replaces the generated Texture sound; its filename appears on the channel. The main button still selects the instrument.

**Record microphone** in the same dropdown opens a recording dialog and asks for microphone permission. **Stop** loads the recording as the Texture sample; **Cancel** discards it. Recordings stop automatically after five minutes. Microphone audio is not monitored through the speakers. If a browser blocks microphone access for a local file, use the HTTPS app or localhost.

The middle knob on **Step** selects sequenced sample playback: **Restart** (default) cuts the previous playback at each new note and restarts the file; without another note, it continues to the end. **Full** ignores notes while the clip is playing. After it finishes, the next note triggers a fresh playback. Neither mode overlaps copies or repeats automatically without a note. In **Keys** mode, samples always restart on each key press and fade out when that key is released, regardless of the sequencer setting. **Stop** stops sample playback. Samples use a fast envelope and neutral effects by default. Quiet recordings receive bounded gain without changing their pitch. Samples follow the channel's envelope/effects. The sample Pitch knob is centered at **0 st**, with a range of **−24 to +24 semitones**. The track's note when loaded is its original-speed root, and played keys transpose from that root. Pitch changes playback speed, so higher pitch plays the whole file faster and lower pitch plays it slower. Choose **Use Texture** to return to the built-in sound. Loading a sample and returning to Texture can both be undone. On **Step**, the Texture **Sound** knob cycles through the three built-in Texture sounds and the 12 most recent imported samples or microphone recordings. Recent samples remain available in this browser after a reload. Knobs that choose from short lists—sounds, note lengths, and playback modes—advance incrementally with small turns instead of following the hardware knob’s absolute position. Mouse drags use the same incremental behavior. Project files include the currently selected sample, rather than the whole recent-sample library.

Samples are stored locally in this browser and embedded in saved `.dimi.json` project files so they can be reopened elsewhere. No audio is uploaded. If the browser cannot persist the sample, save a project file to retain it.

## Send notes and clock to Ableton or hardware

1. Open **MIDI mapping & shortcuts**, click **Connect output**, and select a destination under **Send to**. Output is off until you select a port. Controller LED ports are excluded from this destination list.
2. Leave **Notes** and **Clock** checked to send both. Uncheck **Local sound** to hear only the receiving app or synth; this mutes browser monitoring without changing outgoing MIDI, track faders or WAV recording. This preference is remembered in this browser. **Play** sends MIDI Start and clock at 24 pulses per quarter note; **Stop** sends MIDI Stop and releases outgoing notes. Keys mode also sends live notes.
3. Instruments use separate MIDI channels: Kick **1**, Clap **2**, Hat **3**, Metal **4**, Bass **5**, Stab **6**, Pad **7**, Texture **8**. Notes preserve their stored pitch, length, and velocity. Faders send MIDI CC7 volume on the corresponding channel.

**Ableton on Mac:** Enable **IAC Driver → Device is online** in **Audio MIDI Setup → MIDI Studio**, then select that bus in MIDI DIMI. In Live's MIDI settings, enable **Track** and **Sync** for the bus's **input**. Select the bus and instrument channel as **MIDI From** on an instrument track, and arm it or set Monitor to **In**. Enable **EXT** in Live so it follows MIDI DIMI's tempo and Start/Stop. Do not enable Sync output back to the same bus. See Ableton's [virtual MIDI bus setup](https://help.ableton.com/hc/en-us/articles/209774225-Setting-up-a-virtual-MIDI-bus) and [MIDI synchronization guide](https://help.ableton.com/hc/en-us/articles/209071149-Synchronizing-Live-via-MIDI).

**Hardware:** Select a connected USB MIDI synth or MIDI interface output. Set the receiving synth's MIDI channel to the desired instrument channel, and enable external MIDI clock on the receiver. A hardware mixer needs a MIDI clock input or another supported sync connection to follow tempo; an audio input alone cannot receive MIDI clock.

MIDI DIMI is the tempo leader in this version. It sends MIDI notes and clock, not its generated audio or effect processing. Use Record Audio for the internal sound, or load instruments in Ableton/the external synth for outgoing notes. Keep the browser in the foreground for reliable scheduling; hardware and browser timing still need to be tested in your setup.

## Launch Control XL

Use a desktop browser with Web MIDI support, such as Chrome. Plug in the controller, click **Connect MIDI**, and allow access. Select Factory template 1 on the MK1 or MK2, or use the DAW port on the XL 3.

The upper row selects tracks. The lower row toggles eight steps at a time or plays notes in Keys mode. Track arrows move through step groups or change octaves. Faders set track levels. Send Select or Page buttons cycle through **Mix**, **Tone**, **Mod**, **Env**, and **Step** for effects, modulation, and envelopes.

## Phone and tablet

- **iPhone and iPad** — For a hardware MIDI controller, open [MIDI DIMI](https://vuxanov.github.io/MIDI-DIMI/) in [MIDIWeb Browser](https://apps.apple.com/us/app/midiweb-browser/id6757226617). Connect the controller, then tap **Connect MIDI**. If button lights are missing, open **MIDI mapping & shortcuts**, choose the controller under **LED output**, and tap **Test lights**.
- **Android** — Chrome for Android supports [Web MIDI](https://developer.chrome.com/blog/web-midi-permission-prompt). Open the HTTPS app link in Chrome, connect the controller, and allow MIDI access when prompted. MIDI DIMI has not been tested with an Android controller setup.

## Run locally

Open `index.html` in your browser. If your browser blocks MIDI for local files, serve the folder with `python3 -m http.server 8765 --bind 127.0.0.1` and open `http://localhost:8765`.

The app generates sound and saves the current session in your browser.
