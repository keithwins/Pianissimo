# Library: search, filters, tags (and where exercises will live)

October 28, 2026. Keith and Claude.

## What was built

The library list can now be searched and filtered without getting busier.

- **One quiet row:** a search box and a Filter button. The search looks at title, composer, collection, key, era and tags.
- **Filter panel (opens only when asked):** composer, era, key, meter, tempo, collection, and tag chips. Each choice shows how many pieces it would give, given the other filters. Once set, filters show as small removable chips; nothing shows at all until then.
- **With fewer than eight pieces** the whole row stays hidden.
- **Tags button on each row** opens a small editor beneath it.

## Facts and tags

- **Facts** are read from the score when it comes in, never typed: key, meter, tempo marking (only when the score gives one). They are kept with the library entry. Era is looked up from the composer's name at display time, so the table can grow without re-reading any scores.
- **Key** uses the score's key signature to find the pair of keys (major and its relative minor), then picks between them from how long each note sounds and where the bass comes to rest. The written mode is only a weak hint, because some converted scores label minor pieces "major".
- **Tags** are your own words. They live in the piece's sidecar: `tags` (a list of strings) and `tagsRejected` (suggestions you turned down). A typed tag reuses the spelling of an existing one ("stride" becomes "Stride").
- **Suggested tags** come from the notes: scale runs, arpeggios (broken-chord figures), repeated notes, octaves, chords, wide stretches, hand crossing, ornaments. Only the strongest three are offered per piece; More… shows the rest. Keep makes one yours. × dismisses it, and it is not offered again (↺ brings it back). Suggestions are never written to the sidecar unless you keep them, and they count for filtering and search.
- If the folder can't be written to, tags wait in this browser and go into the sidecar next time it can.
- Library entries are re-read once after this change (entry version 5) to pick up the facts.

## Exercises (built, v1, Oct 28)

- Exercises are generated: a material (major, natural and harmonic minor, chromatic, major/minor/dominant-seventh arpeggios) plus a pattern (plain, in threes, in fours, thirds, step and back, turns, skip, with the octave) plus key, hand, reach (1-3 octaves) and direction. Each is written as a small two-staff score and played through the same falling notes, staff, fingering and keyboard. Nothing is stored per key.
- Two families: **pitch-path** patterns (follow the scale/arpeggio) and **fixed five-finger** patterns (five-finger major/minor, patterns of finger numbers, the left hand mirrored).
- They sit in the **one shared list** with an Exercise badge and a Type filter. Tapping a row opens a quiet setup sheet (key, hands, pattern, reach, direction, Start). Once running, a small ‹ key › control in the title bar moves to the next or previous key in circle-of-fifths order, keeping the tempo.
- Scale fingering follows the standard thumb-position tables (checked against textbook fingering in all 12 keys, both hands); arpeggios use 1-2-3 (and 1-2-3-4) right hand, 5-3-2-1 left hand; both can be edited with the usual fingering editor.
- Not yet: "drill this pattern" from inside a piece, "pieces using this drill", the "ready for you" nudge, melodic minor, pentatonic, diminished sevenths, parallel thirds/sixths blocks, reading and ear exercises.
