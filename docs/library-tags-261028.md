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

## Exercises (not built yet; the plan)

- Exercises are generated patterns: a pattern, plus key, hand and tempo, shown through the same falling notes, fingering and keyboard. Nothing stored per key.
- One pool, two doors: browse by skill on their own, or from a selected passage in a piece ("drill this pattern"), and from a drill back to the pieces that use it.
- They share the tag vocabulary above, so matching a passage to its drills is just matching tags. Exercises only need tags for the kind of pattern and the skill it trains; key, hand and tempo are chosen when starting.
- Menu and gentle nudge together: everything is always listed, with a quiet "ready for you" highlight on top.
- Open question: whether pieces and exercises share one list (a "type" filter and a small badge) or sit side by side. Leaning toward one list, since a search for "arpeggio" then finds both.
