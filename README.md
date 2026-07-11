# Pianissimo

A supportive piano learning system: MIDI as ground truth, cameras and coaching as commentary, and a lasting memory of *your* hands on *this* instrument.

Pianissimo is the studio. Optional faces of the same system:

- **Bard** — conversational coach and practice storyteller
- **Twin** — quantitative self-model (timing, touch, habits, progress)

North star piece: regain (then surpass) a clean *Maple Leaf Rag* and use that loop to learn good craft habits—not merely hit notes.

## Status

Early capture. Vision, architecture, hardware notes, and roadmap live in [`docs/`](docs/). Implementation starts with a **MIDI + screen coach** loop on an always-on Linux host.

## Docs

| Doc | What it holds |
|-----|----------------|
| [Vision](docs/VISION.md) | Pedagogy, joy, twin/bard, feedback philosophy |
| [Architecture](docs/ARCHITECTURE.md) | Host roles, data paths, latency budget |
| [Hardware](docs/HARDWARE.md) | RD-88, USB vs DIN MIDI, Pi4, ESP32 LEDs, cams, Quest |
| [Sensing](docs/SENSING.md) | MIDI resolution, video, sync |
| [Corpus & library](docs/CORPUS.md) | Scores, MIDI datasets, your shelf |
| [Roadmap](docs/ROADMAP.md) | Phased build; what not to do yet |
| [Session schema](docs/SESSION_SCHEMA.md) | Memory / logging shapes |
| [Decisions](docs/DECISIONS.md) | Why we chose USB-MIDI, defer Quest, etc. |
| [Capture index](docs/CONVERSATION_CAPTURE.md) | Map from conversation themes → docs |
| [Sync & topology](docs/SYNC_AND_TOPOLOGY.md) | Laptop at keys vs desktop; Matrix vs Syncthing |
| [Mint setup](docs/MINT_SETUP.md) | Commands to run on the practice laptop |

## Principle in one line

**MIDI is law; video is commentary; LEDs/haptics are attention; the twin is memory.**

## License

See [LICENSE](LICENSE).
