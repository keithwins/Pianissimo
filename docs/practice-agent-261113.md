# A practice agent: design note

November 13, 2026. Keith and Claude. Nothing here is built yet.

## The idea

Say to an agent, by voice or typing: "I want to learn The Entertainer, but I'm a rank beginner: look at what I can do and help me get there from here," or "I want to fall in love with playing, reading included: help me find out how." The agent works from the player's own record and uses Pianissimo's own actions to build the practice. Agents can be swapped for better ones as they arrive; the record and the tools are what carry on. In Better Angels terms it is an angel: a chartered relationship with one player, proven by that player's history.

## What Pianissimo already has for it

- **The record:** every note, sealed; measured passes (timing, stumbles, touch, wrong notes); bests per item; points. This is what "look at my skill set" reads.
- **Actions:** practice lists, sections, Drill this (scales and patterns in a piece's key), hard-moves drills, transposing, games with per-player levels, the coach card.
- **A bridge:** "Copy for Claude" already hands a piece's analysis to a chat.

## Two ways in

1. **Claude in Chrome, now.** It can read the Pianissimo page and press its buttons. To make that sturdy rather than menu-clicking, Pianissimo publishes a plain summary for agents (recent passes, bests, stuck spots, lists, the open piece and its analysis) and a few named actions an agent can call (propose a list, open an item, start a drill, set the coach).
2. **An MCP server, later** (Model Context Protocol: the standard way to give an AI agent tools), on the Pianissimo laptop or Ambient Angel, exposing the same summary and actions, so any agent can use them, by voice from a phone included.

Both use the same summary and actions, so the first isn't wasted when the second comes.

## The design rules

1. **Only the next step is planned.** A twelve-week plan dies on the first bad week. The goal stays fixed; each session the agent works out the next session's list from the record. Starting again costs nothing and carries no reproach.
2. **The agent proposes; the player accepts.** Every change the agent wants (a list, a drill, a setting) is shown with its reason and accepted or refused, and the proposal and answer go into the record. No covert authorship.
3. **Anchored to the player's own reasons**, kept in their words, not to points or minutes. The agent also asks how practice felt, not only what was measured, and takes the answer seriously.
4. **A map of skills, not just a hard piece.** "From here to The Entertainer" means: syncopation, left-hand stride leaps, octaves, ledger lines, each a ladder of smaller exercises. Pianissimo's analysis already finds a piece's hard moves; what's missing is linking each to the ladder leading up to it.
5. **Fast things stay in Pianissimo; judgement goes to the agent.** Anything that must happen within a passage (finding a stuck spot, looping it) is ordinary code. The agent decides session-level things: what today, when to switch, when to stop.

## Micro-practice: the smallest place it breaks

How Keith learns: find the smallest sequence that fails (a thumb crossing, a change between two hand shapes), drill it for a few minutes, then go back to the rest. Most of it can be automated:

- **Find the spot** from how the passes actually went: the step where stumbles and wrong notes gather over recent passes. (The hard-moves drill finds difficult places from the music; this finds them from the playing, which is the better signal.)
- **Offer a micro-loop:** that transition plus one note before and after, so the joins are practised too. The coach: "Stuck spot: bar 5, the thumb crossing. Loop it?", one tap.
- **Fold it back:** after a few clean, steady passes of the micro-loop it widens to the section by itself. If the spot breaks again, it's offered again.
- This needs each pass to keep where its stumbles and wrong notes were (step numbers), not only how many.

## Wobbles: reading the stuck place in variations (Keith's idea, better than a plain loop for reading)

Play through once or a few times. Where it stumbled, the next pass inserts small variations of the stuck cell (the two or three notes around the trouble), moved within the key: one step up, one down, then 1 up 2 down, 2 up 1 down, 2 up 2 down. Then it rolls back into the piece a note or two before the spot, or carries on the pattern if it's still stumbling (with a cap, so it never traps you).

- A loop played six times gets memorised and stops being read; variations that shift each time can't be, so they must be read. And it happens inside the flow of the piece, with no stopping to set up a drill.
- **The fingering planner makes the templates; watching the playing drives the response, pass after pass.** A variant must keep what made the spot hard: a thumb crossing must stay a crossing. Variants that become an easy five-finger position are dropped. Moving by a step changes where the black keys fall, so the same motion is met in slightly different forms, which makes it sturdier.
- **Which response, from the kind of stumble:** a long pause before correct notes is usually reading or deciding: wobbles. Wrong notes, or unevenness right after: usually the fingers: the plain micro-loop. The record can tell them apart.
- **A wrong note is itself a stuck spot.** With strict Wait for me, a wrong note backs up and replays the motion; the same spot failing twice starts the wobbles there.
- **Wait for me first** (no tempo, so insertion is simple). In playback the inserted notes must fit the beat and appear on the staff in time; the hard-moves drill's fragment building can be reused.
- **As a game, away from any piece:** slow hand-position shifts with reading required. A five-finger position shows on the staff, moves up a step, down two, and so on; you read and play each.

## Talking with the agent at the piano

The microphone here is for speech with the agent. Hands are busy at the piano, so voice is the natural channel, and the agent follows the playing live through the record.

- **It speaks between passes**, the coach card's rule: never inside a passage.
- **Listening:** the piano itself would set off speech detection, but Pianissimo knows from MIDI exactly when notes are sounding, so the microphone is ignored during notes and listened to in the gaps. For a deliberate "I want to…", a spare pedal or a key combination works as push-to-talk.
- **"Held"** comes from continuity more than from the voice: knowing yesterday's work, the player's own reasons, noticing a return after days away, and keeping it short.

## Wobbles and good reading habits

Fluent readers keep their eyes ahead of their hands, a beat to a bar. Wobbles that appear only just before they're needed would train note-by-note reading, the habit to escape. So:

- Wobbles are written into the staff itself, in the piece's key, rhythm and notation, not a separate pop-up: read the same way as the piece.
- They appear at least a bar ahead and stay; the distance grows as the player improves, deliberately stretching the eye-hand span.
- A small mark shows a variation is coming, so it isn't a jolt.
- No keyboard hints during wobbles (the eyes would drop to the hands).
- The pulse goes on: in playback the tempo may ease, never stop.
- Warm, not gamey: a quiet "again, a step up", not dings.
- Wobbling scales and exercises is an option, not the default.

## Learners, parents, teachers, friends

The learner owns the record; everyone else has a slot with its own permissions:

- **Parent:** progress, rewards, wish lists (the parent code exists already).
- **Teacher:** the detailed record; assigns pieces and lists, sets wobble and strictness options, comments.
- **Friend:** summaries, boards.
- **Agent:** one more slot.

Teachers, parents and agents all act the same way: they **propose**, and the learner (or a parent, for a child) accepts, with both in the record. Built once, that serves all of them. Moving data between computers is the harder part: a shared folder per learner and teacher first; a server later (the same ladder as witnesses and live scoring, see docs/coach-and-points-261113.md and the session log note).

## First slice

- Pass lines record where stumbles and wrong notes happened.
- Strict wrong-note handling in Wait for me.
- The stuck-spot finder, with wobbles and the micro-loop, in Wait for me.
- The agent summary and named actions in the page, read-only except **propose a practice list**, which the player accepts or refuses.
- Try "help me get to The Entertainer" with Claude in Chrome, and learn what an agent actually needs before giving it more.

## Further on

- Measuring passes in playback, against the beat, so the record shows more than Wait for me.
- Voice in Pianissimo itself (on-device speech, or through Ambient Angel), if talking to Claude separately proves clumsy at the piano.
- An agent per player in a family, each with its own record and permissions.
