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

## First slice

- Pass lines record where stumbles and wrong notes happened.
- The stuck-spot finder and micro-loop in the coach.
- The agent summary and named actions in the page, read-only except **propose a practice list**, which the player accepts or refuses.
- Try "help me get to The Entertainer" with Claude in Chrome, and learn what an agent actually needs before giving it more.

## Further on

- Measuring passes in playback, against the beat, so the record shows more than Wait for me.
- Voice in Pianissimo itself (on-device speech, or through Ambient Angel), if talking to Claude separately proves clumsy at the piano.
- An agent per player in a family, each with its own record and permissions.
