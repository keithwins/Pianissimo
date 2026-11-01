# Exercise editor, and making a pattern by playing it (an idea, not built)

November 1, 2026. Keith and Claude. Nothing here is built yet; this is so the idea is kept.

## Why

Exercises are the part of Pianissimo that can grow without limit: every scale, arpeggio, finger pattern, trill figure or "play this line in all twelve keys" is one more exercise. Today the kinds and patterns are written into the page by hand. People should be able to make and change their own, and share them.

## What already exists (and is reused)

- **Patterns are already data.** Each pattern in the Pattern drop-down is a short list: "which steps along the path to play in each group" (plain, in threes, in thirds, turns…). Five-finger patterns are lists of fingers.
- **Kinds of exercise** (major scale, minor arpeggio, five-finger position…) say what the path is, which fingering planner to use, and which options apply.
- **One description of the options per kind** (`exRows`) feeds both the library sheet and the settings menu beside the key stepper, so a new option shows in both.
- **Rebuild with new settings** (`exRebuild`) keeps the tempo and the rest.

## What one exercise definition needs

- **Material:** a scale, an arpeggio, a shape you define, or the notes you played.
- **Pattern:** which steps in each group, and whether it follows the scale or keeps fixed distances (see the open question below).
- **Fingering:** worked out automatically (as now), or given note by note, with "repeat in each octave".
- **Turnarounds:** what happens at the top and bottom: reverse, repeat the top note, jump back.
- **Ornaments:** trills (alternate two notes a number of times), mordents, turns, and similar figures.
- **Defaults:** hand, reach, direction, tempo.
- **Name, a short description, and tags** in the same vocabulary as pieces, so a piece can lead to a matching drill and back.

## The editor

- Opened from the exercise menu in the practice view ("Make one like this", "Edit this one") and from the library.
- It stays to steps, fingers, turnarounds and ornaments. It is not a score editor.
- Each change plays back at once, in the key shown, on the keyboard and falling notes.

## Making a pattern by playing it (record, then generalize)

The idea: play one short figure on the keyboard, and Pianissimo turns it into an exercise that can be played in all twelve keys.

1. **Record.** The keyboard's notes, timing and strike strength are already logged in the session record; this is the same stream, taken for one short take.
2. **Read it.** The notes become steps and distances; the timing is kept as played, or tidied to a grid you choose; the fingering is suggested by the planner and corrected by you in the fingering editor.
3. **Say what it is.** Follows the scale, or keeps the same shape in every key. Both are shown as a preview in three keys and you pick.
4. **Save** as an exercise, with a name and tags.

### Is it a can of worms? Small, if kept small

Kept to one short figure (a bar or two), it is manageable. The real difficulties are:

- **Intent is ambiguous from one sample.** The same notes can mean "up the scale" or "this shape". The preview in several keys settles it.
- **Human timing is messy.** Offer "keep my timing" and "tidy to a grid", and never throw the original away.
- **A keyboard does not know your fingers.** Suggest, then let you correct. A camera could confirm later.
- **Two hands from one keyboard.** Split at middle C as for MIDI files, and let it be changed.
- **A wrong note in the take.** Re-record, or trim the start and end; a full piano-roll editor is out of scope.
- **"Sampler" can mean two things.** Recording and replaying *notes* (MIDI) is the plan here. Recording *sound* is a different and much larger thing (microphone, delay, storage, rights) and is not part of this.
- **Scope creep.** "Record my whole practice and play it back" is a separate feature, closer to the session record.

## Open question to settle first

Does a pattern follow the scale or keep fixed distances? "Three steps up the scale" changes shape between keys; "a third, then a fifth" does not. Scales and arpeggios use the first; jazz material and transposed lines need the second. Each pattern should say which it is.

## Sharing and safety

Exercises are small files with only allowed fields and size limits, so they can be shared safely (the same approach is intended for shareable games later). They carry no music from anyone's scores, only steps and rules.

## Suggested order

1. Move the built-in patterns into the same file format that user patterns will use.
2. An editor for steps, turnarounds and fingering, with live preview.
3. Ornaments.
4. Record by playing, for one short figure.
5. Sharing, and "Key" on any piece (transposing a whole piece or solo through all twelve keys).
