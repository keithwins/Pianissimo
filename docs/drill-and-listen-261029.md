# Drill from inside a piece, and listening (Wait for me without MIDI)

October 29, 2026. Keith and Claude.

## Drill this section

- In the section menu, **Drill this section** looks at the notes of the current section (or the whole piece) and proposes an exercise: which hand, scale or arpeggio, which key, how many octaves. A five-finger pattern is proposed only when the notes fit one closely.
- The proposal opens as a small card with plain-language reasoning. Material, key, pattern, hands, reach and direction can all be changed before **Start this drill**.
- While the drill runs, **← Piece** in the title bar returns to the same piece and section. The ‹ key › control still steps through keys.
- It is a guess from the notes (key fit, scale-run share, arpeggio share, hand span), never a claim about what the music "is".

## Listening (microphone Wait for me)

- In the Wait menu, **Listen with microphone** makes Wait for me work without a MIDI keyboard, on any device with a microphone. The choice is remembered; the microphone starts when Wait for me is turned on and stops when it is turned off or the page is left.
- Nothing is recorded or sent anywhere. Sound is analysed in the page and thrown away.
- Detection looks for the fundamental of each of the 88 keys with a fine frequency analysis, requires a sudden rise (a new strike) and rejects overtones of louder lower notes, neighbouring semitones and octave-below notes. Below G3 it also follows the second overtone, since low notes are too close together to separate by the fundamental alone.
- A **sensitivity** slider and a level bar are under "More" in the same box.
- Only the lit notes can advance the lesson; wrong notes are ignored. Chords need all notes. The other hand's part still plays for you when that option is on, and that sound is masked from the listener.

## Known limits

- Tested with synthetic piano recordings (single notes, chords, quiet playing, noise and hum, deliberate wrong notes), not yet with a real piano in a real room.
- Fast repeated notes are not caught; there is about 0.2 s delay; extra-note counting is off in this mode.
- A soft melody note played over a much louder lower note may be taken for an overtone.
- Low notes are the least certain.

## Also changed

- The live timing readout is hidden (`SHOW_TIMING = false`). Timing is still measured and logged. It will return, probably as something more visual and game-like.
