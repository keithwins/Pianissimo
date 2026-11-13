# The coach, and points (first version)

November 13, 2026. Keith and Claude.

## Measuring a pass

In Wait for me, Pianissimo knows which notes each step wants and when you played them, so each pass through a section is measured and goes into the session record as a `pass` line:

- **Timing:** each step's gap since your last, against the beats the music says pass. Steady playing keeps that constant at whatever pace you choose; its spread, as a percentage, is how uneven you were (lower is steadier), and its middle is the tempo you really played. A gap more than 2½ times your usual is a stumble, not unevenness. Steps the other hand plays for you are left out.
- **Touch:** the spread of your key velocities (0–127; lower is more even), and their average.
- **Accuracy:** wrong notes.

Only Wait for me passes are measured for now. Playing along with playback, or freely, comes later.

## Points, rules version 1

A first draft. Points are always worked out from the `pass` lines, so when the rules change, everything is counted again (Settings, Coach, **Count again from the record**).

- Each pass earns a little (10), less with each repeat of the same thing in a day: the 10th repeat earns about half.
- The first two passes of an item each day are warm-up: wrong notes there cost nothing.
- The real points are for moving your best on that item, on clean passes: first clean pass 50; steadier than your best 30; faster than your best and about as steady 30; a more even touch 20.
- Back to an item after 3 days or more, still clean, in the first passes of the day: up to 50 (retention).
- Moving on to something not played in the last 5 minutes: 3.
- Clean and steady (timing within 12%) on 3 different days: mastered. Everyday points on it drop to a third; a return after days away still earns in full.

An item is a section of a piece (in its key, with the hands Wait for me is set to) or an exercise with its settings.

Points belong to the player in Who's playing. The running total kept in the browser is only a convenience.

## The coach card

- Speaks at the end of a pass, never in the middle of one, and fades by itself (it stays while the pointer is over it; ✕ hides it).
- Drag it anywhere; near an edge it sticks to the edge. Settings, Coach, **Put the card back** returns it to the corner.
- Settings, Coach: on or off; after each pass, only when something changes (a new best, a wrong note), or a summary when you stop; one line or more; and which of wrong notes, timing, touch, tempo and points it mentions.

## Also in this update

- Every recorded line is kept at once in the browser until it's safely written, so closing the page abruptly loses nothing.
- The middle and soft pedals, and release velocity, are now recorded.

## Next

- Measure passes when playing along with playback, against the beat.
- Dynamics against a shape (a crescendo up, diminuendo down), not only evenness.
- Tune the rules from real use.
