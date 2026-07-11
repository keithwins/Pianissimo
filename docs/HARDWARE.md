# Hardware

Inventory and decisions for the practice studio. Update this file as gear is confirmed.

## Keyboard — Roland RD-88

Stage piano with weighted action. Rear panel has a USB jack **marked Computer** (confirmed), plus other ports including classic MIDI as applicable.

### Proven path

The **USB Computer** port already worked as a MIDI source into a phone running **flowkey** (piano learning app). That is exactly the class-compliant USB-MIDI path Pianissimo wants—same idea, Mint laptop instead of phone/app store coach.

### Why two kinds of “MIDI plugs”?

They are different histories of the same idea:

| Port | What it is | Typical use |
|------|------------|-------------|
| **USB Computer** (confirmed label) | USB-MIDI device; one cable to phone/PC/laptop | flowkey (done), DAWs, Pianissimo host |
| **Other USB** (if present) | Often not “second MIDI out”—may be storage/host-type roles; don’t assume | Check panel / manual before buying splits |
| **5-pin DIN MIDI In/Out/Thru** | Classic serial MIDI (~31.25 kbaud); needs MIDI cables / interface | Hardware synths, pedals chains, microcontrollers |

So: not two random USB shapes for the same job—**USB Computer to the host** vs **DIN to other MIDI hardware**.

### USB-MIDI vs DIN — what should Pianissimo use?

**Prefer USB Computer → Mint host** for this project. Already validated in the wild via flowkey.

| | USB-MIDI | DIN MIDI |
|--|----------|----------|
| Cable / interface | Usually one USB cable | Needs MIDI interface or USB-MIDI host on Pi/ESP |
| Latency / jitter | Excellent for interactive software on a PC | Fine for gear; adds interface hop if PC is the brain |
| Clock / setup | OS sees a class-compliant MIDI device | Extra box or UART-MIDI on MCU |
| Multiple consumers | Host can fan-out in software | Hardware thru / merge boxes |
| ESP32 LEDs | Host forwards note events over USB-serial / Wi-Fi / DIN-UART | MCU can listen on DIN In directly |

**DIN still useful** for: ESP32 or Pi that should light LEDs even if the laptop UI is asleep; classic MIDI thru chains; isolation experiments.

**Default architecture:** RD-88 → **USB → Mint** → (optional) forward highlight stream → ESP32 LEDs. Revisit DIN tap if the LED box should run standalone beside the keyboard.

## Always-on host — Linux Mint i7 laptop

Primary development + practice computer; drives coach monitor when in session. See [Architecture](ARCHITECTURE.md).

## Desktop — RTX 5070 Ti

GPU annex on the same Wi‑Fi. Happy and available for offline / heavy vision and Twin jobs; not required for live USB-MIDI coaching. See [Sync & topology](SYNC_AND_TOPOLOGY.md).

## Raspberry Pi 4

Available spare. Good roles:

1. LED / MIDI sidecar (test strip without touching Mint UI)  
2. USB camera bridge or overnight encode/ingest  
3. “Room presence” / status for the studio  

Not required until Mint MIDI + screen loop works—unless DIN/LED prototyping is more fun first.

## LED key guide

Addressable LED strip sized to key spacing (off-the-shelf strips; spacing ironed out years ago in prior thinking). Likely driver: **ESP32** speaking a tiny protocol and/or MIDI.

Deferred until Phase 1 coach UI exists—or parallel prototype if the strip hardware is already on hand.

## Cameras

### Phase order

1. One fixed **overhead / keyboard** camera (phone or USB cam is enough)  
2. Second keyboard angle for orthogonality  
3. Head-mounted or glasses cam for gaze / score vs keys  
4. Wider-baseline stereo headgear for depth / prediction training  

### Stereo headgear candidate

Category example: ~60 fps dual-lens USB stereo modules (~120° class, high horizontal resolution / VR-ish biometric kits). Comfort + **fixed calibration** beat max megapixels. Validate sync to MIDI timestamps before investing in ML depth.

Mount **wider on a visor/headband** only after mono paths are clean; orthogonality helps twin training but fights cables, weight, and calibration early.

## Display

- Spare monitor(s) for drop-note + hand view — **fastest high-value surface**  
- Headset (below) later as morphable / AR surface  

## Meta Quest (candidate)

**Maybe later; not the Phase 1 workbench.**

Pros: immersive coach surface, passthrough overlays, “stage” feeling, detached from desk clutter.  
Cons: IPD/fit fatigue, USB/Wi-Fi streaming plumbing, harder debug loop than a monitor, temptation to build HUD before pedagogy exists.

Place Quest on the roadmap as **Phase 4 display option** after screen + strip feel native. Development stays on Mint (+ this repo); Quest is a client.

## Wearables / other actuators (open, not scheduled)

Wrist bands, IMUs, stimulators—on the table if video cannot capture tension/timing we care about. Do not schedule until Twin has MIDI+video biography for real pieces.

## Mentally reserved shopping list

- [x] Confirm RD-88 USB **Computer** jack (done; used with flowkey on phone)  
- [ ] Note other rear USB / DIN labels (photo into repo optional)  
- [ ] USB cable / powered hub if needed for cam + keyboard on Mint  
- [ ] Overhead cam mount  
- [ ] Addressable LED strip + ESP32 (when ready)  
- [ ] Optional: DIN → MCU for standalone LED mode  
- [ ] Optional later: stereo headcam / Quest  

## Spelling / brand note

README historically typo’d “Pianisimo”; project name is **Pianissimo**.
