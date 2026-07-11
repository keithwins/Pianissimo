# Architecture

## Layering

| Layer | Job | Early tools | Later |
|-------|-----|-------------|--------|
| **Ground truth** | What note / when / how hard | RD-88 MIDI | pedals, more CCs |
| **Body truth** | Hands, posture, gaze | 1–2 keyboard cams | glasses / stereo headgear, IMUs |
| **Score truth** | What should happen | MIDI / MusicXML + drop-note | morphable arrangements |
| **Coach** | What to change *now* | screen + voice | LEDs, haptics, headset |
| **Memory (Twin)** | What you are learning | session logs | personal models |

MIDI is the metronome of truth. Vision comments on *how*. Actuators steer *attention*. Conversation holds *why* and *what next*.

## Host roles

### Always-on Mint i7 laptop (primary development + practice host)

Owns the coherent loop: one clock, one session archive, one UI to the coach monitor. When carried to the RD-88, it remains the **live author of sessions**; a desktop on the same Wi‑Fi is an annex—see [Sync & topology](SYNC_AND_TOPOLOGY.md).

- MIDI ingest + wall-clock timestamps  
- Drop-note / coach UI on spare monitor(s)  
- Practice state machine (“memory of last attempt”)  
- Library (scores, MIDI, recordings, photographed sheets)  
- Camera ingest + sync to MIDI  
- Light landmark / pose inference  
- Bard (local small model and/or remote API)  
- Twin updates (aggregate stats, fingerprints of sessions)

This machine is **not** expected to be taxed by Phase 1–2 if huge VLMs are avoided on every frame.

### Desktop with RTX 5070 Ti (GPU annex)

Confirmed available and healthy. Owns hungry offline work after Syncthing pulls sessions from the laptop—reprocess video, train Twin features, heavy experiments. Does **not** need to be in the live MIDI→screen path. See [Sync & topology](SYNC_AND_TOPOLOGY.md).

### Cheap / good shunts

| Node | Own | Do not dump here early |
|------|-----|-------------------------|
| **ESP32 (+ LED strip)** | Key highlight, next-note glow, error flash, section colors from a tiny note protocol / MIDI parse | Vision, pedagogy, disk archive |
| **Pi 4** (available) | Isolated LED renderer, MIDI bridge/tester, camera spy sidecar, overnight ingest jobs, “always listen” MQTT/status | Full coach UI + heavy ML until Mint path is proven |
| **RD-88** | Haptic instrument; USB-MIDI device | — |

### Cameras

- Prefer **stable overhead keyboard cam** first (best teaching signal).  
- Then gaze/score cam (screen foothold or modest headband).  
- Stereo headgear after mono sync is trustworthy.

### Headset (Meta Quest — candidate, later)

Treat as an optional **work surface / AR coach display**, not the development platform. Mentally phase after screen + strip feel magical. See [Hardware](HARDWARE.md).

## Latency budget

- Visual note feedback: aim **&lt; ~50–80 ms** perceived, or it feels “off.”  
- LED path: keep on microcontroller when possible.  
- Bard speech: may lag; never block the motor loop.

## Data path (logical)

```text
RD-88 --USB-MIDI--> Mint host
                      ├--> session archive (MIDI + clocks)
                      ├--> coach UI (monitor)
                 (opt)├--> ESP32 / Pi --> LED strip
                 (opt)├--> camera(s) --> aligned frames / landmarks
                      └--> Twin + Bard
```

## Privacy

Local capture and archive by default. Cloud models only when explicitly chosen for a session or Bard turn.

## Working rule (dev)

Keep Linux project work on the practice/dev host (Mint or WSL clone of this repo). Avoid editing the same clone from Windows and Linux casually; pick one filesystem home per machine.
