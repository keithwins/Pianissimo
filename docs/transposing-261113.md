# Playing a piece in another key

November 13, 2026. Keith and Claude.

## In use

- Every piece has the key chip in the header, the one exercises already had: ‹ key › and a small menu. ‹ › move the piece a half step at a time, up to an octave either way.
- The menu: **Back to the original key**, and **Suggest fingering again for this key** (your own changes in that key are kept).
- The key you last chose is remembered with the piece. A practice-list item keeps its own key, so the same bars can be on a list in C and in D♭.
- Exercises keep their own key stepper, as before.

## How it works

- The original is never changed. A piece in another key is made from it each time it opens: notes moved and spelled for the new key (G♭ in D♭ major, not F♯), the score moved for the staff, key changes and chord symbols with them. Of two names for a key, the one with fewer sharps or flats.
- A MIDI file has no key written in it, so its key is taken as the major key whose scale holds the most of its notes.
- **Fingering is kept per key**, in the piece's practice file under `keys`. The first time in a key it is suggested once and saved; after that, your edits. The score file keeps the original's fingering. Saving in another key never writes the score file.
- Unsaved fingering edits waiting in the browser are kept per key too, so an edit made in D♭ can't land on the original.
- The drawn staff is cached per key.
- Each change of key goes into the session record.
