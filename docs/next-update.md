# Next update

Things agreed but not built yet. Remove each once it's done.

- **Key colors too faint (Keith, 261113).** Keys marking notes about to be played are tinted with only 32% of the hand colour on white keys (`.wk.hint-r` / `.wk.hint-l`, `color-mix … 32%`), which washes out on his screen. Add a "Key colors" strength slider under Settings, Show (from the faint tint to full colour; raise the default), and right- and left-hand colour pickers that recolour keys, falling notes and staff marks together (stored as overrides of `--rh` / `--lh`; the first piece of colour skins).
- **Intervals, a mode of Landmarks (Keith, 261113).** A note shows; the prompt says "up a 3rd" (or down); play the answer. Teach interval size first (on the staff a 2nd is line to space, a 3rd line to line or space to space), in C. After each answer show both readings side by side: the staff's ("a 2nd, line to space") and the keyboard's ("a half step, E to F"), so it's visible that same-looking intervals can be half or whole steps. Later: in a key (up a 3rd in D major is F♯), naming the interval between two shown notes, hearing two notes and playing them, and stacking 3rds into triads as the bridge to harmony practice.
- **Wrong notes aren't tolerated in Wait for me (Keith, 261113).** Now a wrong note is counted and the player just waits for the right one, so "wrong, correct, go on" is what gets practised. Strict (the default): in a chord, any wrong note means lift and strike the whole chord again cleanly; in a run, a wrong note backs up two or three notes (about a beat) so the motion *into* the note is replayed. A velocity floor (about 10, adjustable) ignores near-silent grazes; strictness is looser or off when listening by microphone. A wrong note also marks a stuck spot (see wobbles).
- **Each pass records where it went wrong (Keith, 261113):** the steps of stumbles and wrong notes, and which kind (a pause before correct notes, or wrong notes and unevenness). Needed by wobbles and the micro-loop.
- **Wobbles, in Wait for me first (Keith, 261113).** See docs/practice-agent-261113.md.

## Offered, not decided

- Library safeguards: pin the three outside libraries (bundle them, or integrity hashes) and size caps on imported files (from the trojan question, 261112).
- Landmarks with key signatures: same positions, the key changes what they mean (F line in D major is F♯), a key at a time.
- Reading aids for the staff: larger staff, fewer bars at a time, tinted landmark lines, wider note spacing, note names that fade.
