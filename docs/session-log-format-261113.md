# The session record: format 1

November 13, 2026. Keith and Claude.

Everything played and done in Pianissimo goes into the session record. It is the honest base for everything built on top: progress views, game levels, scores and points, boards with friends, rewards. Those are always worked out from the record; the record is never worked out from them.

## Files

- In the music folder: `Sessions/Pianissimo_session_<player>_<yymmdd>.jsonl` (no player chosen: `Pianissimo_session_<yymmdd>.jsonl`). One JSON object per line.
- When the folder can't be written, lines wait in the browser and are added to the file later, in their order.
- **Records are only ever added to.** Nothing is edited or deleted in place. A fix is a new line (see `correction`).

## Lines

Each session starts with a header; every other line has `t`, milliseconds since that header, and `e`, what happened.

| e | When | Fields |
|---|---|---|
| `session` | start of a session (new day or player) | `format` (1), `at` (local time), `build`, `player`, `piece` {id, title}, `sound`, `keyboard` |
| `on`, `off` | every key down and up | `m` (MIDI note), `v` (velocity, on); `r` (release velocity, off, when the keyboard sends it) |
| `ped`, `sost`, `soft` | the sustain, middle and soft pedals | `v` (0–127; values between show half-pedalling) |
| `pass` | a pass through a section in Wait for me | `item`, `name`, `steps`, `even` (timing spread, %), `bpm` (tempo played), `stumbles`, `vsd` (velocity spread), `vmean`, `wrong`, `secs` |
| `set` | settings changed | the settings |
| `piece` | a piece opened | `id`, `title`, `bars` |
| `key` | a piece moved to another key | `id`, `tr` (half steps), `key` |
| `play`, `stop`, `panic` | playback | `k` (onset), `bar`, `bpm`, `from`, `to`, `loop` |
| `want`, `got`, `waitsel` | Wait for me | `k`, `bar`, `st`, `m` (notes wanted), `hands` |
| `heard`, `dt` | listening by microphone | `m`, `snr`; `m`, `k`, `ms` |
| `finger`, `fing-discard`, `livefing`, `reach` | fingering | `note`, `name`, `f`, `src`; `id`; `on`; `v` |
| `drill`, `leapdrill` | drills started | `from`, the drill's settings |
| `game`, `round` | games | `game`, `hand`, and per game: `ok`, times (`ms`, `firstMs`…), what was asked and what was played |
| `player`, `wish` | Who's playing | `name`; `got`, `min` |
| `tour`, `help` | the tour, questions asked | `id`, `at`, `of`, `done`; `q` |
| `correction` | a fix to earlier lines | `what` ("player", "removed", …) and the details; nothing earlier is changed |
| `seal` | after each write | see below |

New kinds of line may be added; readers should skip what they don't know. A change to the meaning of an existing field means a new `format` number in the header.

## Seals

Each write to the record ends with a seal line:

```
{ "e": "seal", "v": 1, "dev", "n", "at", "lines", "files"?, "prev", "h" }
```

- `dev`: this computer's (browser's) id. Each keeps its own chain, so machines sharing a folder don't tangle.
- `n`: the seal's number in that chain. `prev`: the previous seal's `h` ("" for the first).
- `lines`: how many lines directly above the seal it covers.
- `h` = SHA-256( `prev` + "\n" + those lines, each with its newline + JSON of { dev, n, at, lines, files? } ), in hex.
- `files`, on a device's first seal only: every session file already in the folder, as { name: [SHA-256 of its first L characters, L] }. History from before sealing began is covered from then on.

Lines that waited in the browser were sealed there; when they reach the file, the new seal covers them, their seal, and the new lines together. Both check out.

`chainCheck()` in the page walks every seal and reports, per device: seals that don't match what they cover (changed), seals whose `prev` is missing (a gap: removed, or still waiting in a browser), and whether the files fingerprinted when sealing began still start the same way.

## What sealing proves, and what it doesn't

- It proves the record wasn't changed after it was written, as long as something outside the file holds the latest seals (a witness: another family computer, Ambient Angel, or a public timestamp). On its own, a file can be rewritten with a fresh chain; a witness is what makes that show.
- It does not prove the playing was real when it was recorded (a computer can play MIDI). That is left alone on purpose: it's the same for every game.
- Next, when wanted: a witness, a "check my history" view, and points worked out from the record.
