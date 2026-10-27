# Pia as a practice partner: design note

October 27, 2026. Keith and Claude. "Pia" is the casual name for Pianissimo.

## The idea in brief

Pia watches you play, finds the small piece you are working on, and drills you on it until it is in hand. Then it joins that piece to its neighbours and moves on. "In hand" is not only "the right notes": it can be timing, loudness, swing, or any other quality, each with its own allowance for that spot in the music. Pia shows how close you are with a quiet, live graphic, and offers odd exercises (everything loud, everything soft, swing it hard) that build control and freedom rather than one correct way to play.

Most of this runs on simple rules inside Pia, instantly and with no outside service. An AI model (Claude, Grok) is an optional advisor for the bigger judgment calls, called from inside Pia with the player's own key. It is never a separate chat window.

## What already exists

- Every key pressed and released is recorded with its time to the millisecond and how hard it was struck, along with the pedal, the settings, and what Pia was asking for. One file per player per day: `Sessions/Pianissimo_session_<player>_<yymmdd>.jsonl` in the music folder.
- Sections can already start and end on any note, not just on bar lines.
- Each piece has its own sidecar file (named in parallel with the score) holding saved sections, fingering, and a practice log.
- Fingering is known for every note (printed or suggested), so Pia can tell where the hand has to move.

## Slices

A slice is the smallest stretch worth practising on its own: one gesture, one hand position, one arpeggio. It is not tied to bar lines.

Pia finds the joints in the score itself:

- rests and long notes
- a change of hand position, from the fingering (a thumb crossing, a jump, a new five-finger position)
- big leaps
- a change of harmony or of beaming

A slice holds one complete gesture between joints. Slices can be joined into longer runs.

## Goals for a slice

A goal is a quality, a reference, and an allowance.

- **Notes:** the right keys, in order.
- **Timing:** the gap between each note and where it should land. There are two references:
  - against the click (absolute: "18 ms late")
  - against your own local tempo (relative: "late compared with its neighbours"), which stays meaningful when you drift slowly or play expressively
- **Loudness:** how hard each note is struck, against a target shape (even, a swell, the melody note louder than the rest).
- **Feel:** swing ratio, staccato or legato length, and so on.

The gap is always measured, even when it is zero. What changes is how much is allowed. Each piece keeps a **tolerance map**: tight in an étude passage, loose in a rubato phrase. A matching loudness map works the same way. Together they say "how good, in which ways, here".

Playing against a metronome is a legitimate reference, and the control it builds is real. It only becomes a problem when it is the only option.

## Sequencing (local rules, no AI needed)

1. Start with the smallest slice that holds a complete gesture.
2. Loop it. When it meets its goals a few times in a row, join it to the slice before, then to the slice after.
3. If it stalls, make it smaller, or switch to a different exercise on the same notes. Don't just repeat the same thing.
4. Raise the goals step by step: notes first, then evenness, then loudness and feel.
5. "Good enough for now" can be the player's call as well as Pia's.

The player can change the rules on the fly: slice size, tolerance, and how many clean passes before moving on.

## Exercises for control

These are variations on the same slice:

- everything loud / everything soft / a swell / a fade
- swing it (light, heavy, absurd)
- all staccato / all legato
- accent every second note, every third note
- slower than comfortable, then faster than comfortable
- hands separately, then together

Being able to play the same notes several ways on purpose is the skill. Hitting one target is not.

## What you see

- A small live readout in its own panel, like the bars or the notation: "last note 18 ms early", with a light, simple graphic of recent notes against the allowance.
- When a goal is met, a brief, pleasant confirmation, and the slice joins the next one.
- A single line telling you what Pia wants: "Left hand, bars 12–13, even sixteenths, soft."

## The AI advisor (later)

- Keys for Claude and Grok are entered in Settings. They stay in that browser on that device, never in the music folder.
- The model is called at natural pauses, not between notes. It receives the piece, the recent playing (the whole note-by-note record is fine, since volume is small), and the per-piece summary.
- It answers with a small plan that Pia can carry out: which slices, which goals and allowances, which exercise, and one line of guidance. Pia does the measuring itself.
- It can pre-load a ready-to-chain list of slices for a piece, or step in when a slice keeps stalling.
- To check: whether xAI's service accepts calls straight from a web page. Anthropic's does, with its documented browser opt-in.

## Data to add

- **Per piece, per player summary file** (rebuilt from the session history; never the only copy): slices found, attempts, timing spread, loudness spread, which goals are met, and the date last practised.
- **Tolerance and loudness maps** in the piece's sidecar.
- **A "where you are" line** at the start of each session record, so anything picking up (Pia or a model) can see the state at a glance.

## Later still

- Cameras on the hands, to see fingering and hand shape.
- Eye tracking, at least coarse: keys, falling notes, or notation.
- Getting musicality back into the picture: learning a player's intended shaping and judging against that, not against a flat MIDI grid.

## Build order

1. The calmer layout (dock, menus, settings sheet), with room for a coach line and the timing readout.
2. The live timing readout.
3. Slice finding from the score and fingering; tolerance maps.
4. The per-piece summary and the local sequencing rules.
5. Exercise variations.
6. AI keys in Settings, and the advisor calls.
