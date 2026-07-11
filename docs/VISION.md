# Vision

Pianissimo is a **closed-loop motor apprenticeship** for piano—not a notation app with cameras bolted on.

```text
Sense → Understand → Coach → Feel → Sense again
```

The system follows the learning process with memory of what was just played, how it compares to earlier attempts and to the target, and what coaching historically helped *this* player. Over time it trains the body onto the machine and supports recursive immersion in a musical corpus at increasing depth.

## Goals

1. **Capable mastery of the tool** — RD-88 (or similar): touch, timing, fingering, pedaling, posture, attention.
2. **Capable mastery of the medium** — reading skins (drop-note first), rhythm, dynamics, style, texture.
3. **Self-expression and joy** — once accuracy is stable, coach voicing, swing, tone, phrasing—not only correctness.
4. **A lasting twin** — higher *persisted* resolution than unaided memory: events, video-aligned moments, drills that worked.

## Naming

| Name | Role |
|------|------|
| **Pianissimo** | Product / studio / repo |
| **Bard** (optional face) | Voice that coaches, explains, remembers stories of practice |
| **Twin** | Silent quantitative self-model; no chat required |

## Interaction that enables growth

Useful loop is not “watch video → get a grade.” It is:

1. **Immediate, local feedback** — e.g. finger late by tens of ms; left thumb tucked; eyes glued to keys.
2. **Morphable difficulty** — same piece, thinner texture, slower, hands separate, then re-enrich.
3. **Self-model over time** — “LH jumps improve when you prep one beat earlier.”
4. **Expression lane** — after stability, coach musical intent.
5. **Co-exploration** — human + a few specialized AIs (motor/timing vs pedagogy vs practice design), not one oracle.

Watching a screen that watches the hands is powerful when latency is low and overlays are sparse. Dense headset AR can wait until the screen loop already feels like a teaching instrument.

## Feedback layering (anti–topic-creep)

Add channels only until cognitive load rises. Stop when removing a channel would feel like silence missing.

1. Acoustic instrument (RD-88) — already rich  
2. Drop-note / falling-note **screen** — one primary attention sink  
3. **LED strip** — peripheral; eyes can stay on hands/music  
4. Sparse hand overlays (“this finger,” not a HUD novel)  
5. Short voice cues  
6. Haptics / headset AR  

**Rule:** one new channel until it feels native. Screen + strip is already a strong duet.

## AI roles (conceptual)

| Stream | Character | Early fit |
|--------|-----------|-----------|
| Fast motor / timing | Predictable, subtle, low latency | On-device or specialized small models (e.g. Liquid-class ideas) |
| Pedagogy / conversation | Slower, contextual | Bard; can be local or API |
| Vision landmarks | Hands, posture, gaze — event-tied | Light pose over every-frame VLM |

Do not make one model do everything. Prefer **timestamps + landmarks + MIDI** over naive large multimodal inference on every frame.

## North star

Regain *Maple Leaf Rag*: at tempo, clean enough to trust—then use that practice biography as the twin’s first deep corpus.
