# Sensing

What can be measured, at what resolution, and how streams stay aligned.

## MIDI — bedrock for Twin

Typical USB-MIDI path from a stage piano like the RD-88:

| Signal | Practical resolution | Twin / coach use |
|--------|----------------------|------------------|
| Key identity | Discrete MIDI note numbers | Pitch map; LED index |
| Strike force (velocity) | **0–127** (7-bit) | Dynamics, accents, harsh thumb |
| Note-on / note-off timing | Host timestamp (~1 ms ideal; often a few ms) | Rush/drag, duration, rhythm |
| Release velocity | If device sends it | Lift habits |
| Sustain / other CCs | Pedal often 0/127 or continuous 0–127 | Legato, blur, pedaling craft |
| Aftertouch / channels | Model-dependent | Later expressive coaching |

**Implication:** velocity + timing are enough for a powerful first twin. MIDI 2.0 / higher-res velocity can wait until 127-level coaching is boring.

Capture wall-clock (and optionally MIDI clock if used) on the host for every event. Never rely on “frames alone” for note correctness when MIDI exists.

## Audio (optional early)

Microphone or digital audio out can help tone/timbre coaching later. Not required for Phase 1 note accuracy.

## Video

| View | Why | Cadence target |
|------|-----|----------------|
| Overhead keyboard | Hands, fingering, prep gestures | ≥30 fps; 60 fps nicer |
| Second keyboard angle | Orthogonality, occlusion | Same |
| Face / score / gaze | Attention (keys vs notation) | 30 fps often enough |
| Stereo headgear | Depth, egocentric prediction | 60 fps class when ready |

Prefer **landmark / pose pipelines** tied to MIDI events over continuous heavy VLM chatter.

## Synchronization

Minimum viable sync:

1. Host monotonic clock  
2. MIDI event timestamps on that clock  
3. Camera frame timestamps on that clock (V4L2 / app capture time)  
4. Store offsets for each device at session start  

Later: hardware trigger / shared clock if multi-cam ML needs sub-frame rigor.

## Force / speed / duration from MIDI alone

- **Speed of key travel:** not directly available from standard MIDI velocity (velocity correlates with strike intensity, not a physical m/s reading).  
- **Duration:** note-on → note-off on host clock — excellent.  
- **Strike “force”:** velocity 0–127 — coarse but musically meaningful; combine with audio later if needed.  

Extra sensors (IMUs, key-bed hacks) only if Twin questions outgrow this.

## LED / ESP32 sensing

Prefer LEDs as **outputs**. If the strip board also listens to DIN MIDI, it may log a parallel note stream—but canonical archive stays on Mint.
