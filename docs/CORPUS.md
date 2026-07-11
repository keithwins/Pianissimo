# Corpus & library

Pianissimo should own a **library**: pieces you care about, target MIDI/MusicXML, your recorded attempts, and eventually multi-view video aligned to MIDI.

## Personal shelf (first-class)

- Photograph / scan existing sheet music into the library.  
- Tag by difficulty intent, hand focus, and north-star status (*Maple Leaf Rag*).  
- Prefer pieces you will actually rehearse; depth beats a giant unread pile.

## Online / public resources (MIDI, scores, audio)

Useful starting points (availability and licenses vary—check each use):

| Kind | Examples / families |
|------|---------------------|
| Aligned piano audio + MIDI | [MAESTRO](https://magenta.tensorflow.org/datasets/maestro) |
| Large MIDI corpora | GiantMIDI-type collections; other open MIDI dumps |
| Scores / MusicXML / MIDI | MuseScore ecosystem; IMSLP (public domain); other open score sites |
| Tutorials | YouTube (often overhead + face; sync and rights are messy) |

**Multi-view video + clean MIDI** as a ready-made open dataset is rarer than MIDI-only. Plan to **grow your own multi-view corpus** as the precious asset; borrow public MIDI/scores aggressively.

## Library roles

1. **Targets** — what “good” looks like for a piece (MIDI, optional reference audio).  
2. **Skins** — drop-note, staff, simplified textures (morphs of the same piece).  
3. **Attempts** — your sessions (see [Session schema](SESSION_SCHEMA.md)).  
4. **Drill extracts** — bars, hands-separate slices the coach reuses.  

## Recursive immersion

Same piece through increasing depth:

listen → hands separate → slow loop → tempo ladder → full texture → expression pass  

Twin tracks *your* curve through that path, not generic leaderboards.

## Ingest backlog (living)

- [ ] Inventory physical sheet music worth photographing  
- [ ] Import a clean *Maple Leaf Rag* MIDI / MusicXML target  
- [ ] Decide local folder layout under `library/` (when scaffolded)  
- [ ] License notes for any redistributed MIDI/scores  
