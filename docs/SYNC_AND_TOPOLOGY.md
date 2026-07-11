# Sync & studio topology

The practice laptop at the RD-88 will often be **away from the desktop** while both sit on the **same Wi‑Fi**. Treating Pianissimo as a **boba-process instantiation**—a learning instant with memory, companioning, and recursive depth—means deciding what must stay coherent across rooms without turning every practice into a network science project.

## Roles when two computers exist

| Machine | Role |
|---------|------|
| **Mint laptop (at keyboard)** | Practice host: MIDI, cams, coach UI, **authoritative live session** |
| **Desktop (elsewhere) — RTX 5070 Ti** | Dev desk + **happy GPU annex**: heavier vision/training, offline Twin jobs, agent/Bard side work, corpus browsing; pulls sessions via Syncthing |
| **Always-on Matrix server** (existing) | Human/agent messaging, presence, “salon”-style coordination—not the session media store |

During a session, prefer **one writer** for Twin archives: the laptop. Desktop consumes or merges later.

### GPU split (5070 Ti is happy — use it)

Live coaching at the keys should stay snappy on the Mint i7 without depending on the desktop being awake. Shunt **batch / hungry** work to the 5070 Ti when sessions have synced:

- Offline landmark reprocess / better pose models over recorded video  
- Training or fine-tuning personal Twin features  
- Big corpus / embedding jobs adjacent to boba-style indexing  
- Experimenting with heavier VLMs on *clips*, not on the live 60fps loop  

Optional later: LAN inference RPC (laptop streams landmarks request → desktop answers). Not required for Phase 1—Syncthing + overnight jobs is enough.

## What to sync (and with what)

| Payload | Best tool | Why |
|---------|-----------|-----|
| **Code / docs** (`Pianissimo` git repo) | `git` ↔ GitHub | Already authenticated; source of truth for software |
| **Session recordings, library binaries, Twin JSON** | **Syncthing** (or scheduled `rsync` over LAN) | Same Wi‑Fi, peer-to-peer, good for large/local files; no GitHub bloat |
| **Practice intent / “what we’re working on” / Bard chat continuity** | Matrix room (or bridge into boba Salon patterns) | Messages, links, small JSON stubs, wake-ups—not multi‑GB video |
| **Live MIDI / 60fps video** | Stay local on laptop | Do not stream raw session A/V through Matrix |

### Matrix: use it, don’t abuse it

**Good:** “session started / stopped,” piece name, tempo, notes to future-you, agent handoffs, linking a session_id, lightweight boba-style orientation.

**Bad:** pushing MKV/MIDI dumps through Matrix as the sync plane. Bridges get fragile; media caps hurt; you’ve already got Wi‑Fi plus disks.

So: **Matrix for the learning conversation layer; Syncthing/git for the bits.**

## Recommended Phase 0 LAN setup

1. Both machines: install **Syncthing**.
2. Share two folders (laptop ↔ desktop):
   - `Pianissimo-library/` — scores, targets, photographed sheets  
   - `Pianissimo-sessions/` — recorded attempts (grow carefully; disk fills fast)
3. Repo code: clone on both; **commit/push from whichever machine edited**; pull before sessions if you edited docs on the desktop.
4. Optional Matrix room `#pianissimo` (or under existing boba/salon space): session breadcrumbs only.

Conflict rule: if both sides edit the same session folder, Syncthing will quarrel—so **laptop owns sessions while practicing**; desktop is read-mostly until the laptop is idle.

## Boba-process instantiation (how this maps)

Pianissimo is not a random app beside boba; it’s the same process applied to craft:

| Boba-ish concern | Pianissimo instantiation |
|------------------|---------------------------|
| Memory / corpus | Twin session archive + piece library |
| Companion / braid | Bard (+ later multi-agent coaches) |
| Situated practice | Laptop at the instrument (the “learning instant”) |
| Cross-context continuity | Matrix crumbs + Syncthing body + git mind |
| Recursive depth | Morphing the same piece through difficulty skins |

Distance from the desktop is fine if continuity is explicit: you take the **practice host** to the keys; the desktop remains a **studio annex**.

## Explicitly defer

- Real-time bidirectional remote desktop as the main UX (laggy for MIDI coaching)  
- Making Matrix the Twin database  
- Cloud sync of every practice video by default (privacy + cost)

## Checklist

- [ ] Syncthing on Mint laptop + desktop; library + sessions folders  
- [ ] Same `Pianissimo` git remote on both; habit: pull before practice if docs changed  
- [ ] Optional Matrix room for session breadcrumbs / boba handoff (**reuse existing homeserver** — do not install a second Matrix)  
- [ ] Confirm laptop is the only writer during practice  

## Sit-at-both-machines setup (do once downstairs)

No new Matrix server. You already have one. Crosstalk upstairs = Syncthing + git (+ Matrix client if you want crumbs).

1. **Desktop + Mint:** install Syncthing (`sudo apt install syncthing`), start it, open the Web UI, add each other as devices (same Wi‑Fi).  
2. Create matching folders on both, e.g. `~/Pianissimo-library` and `~/Pianissimo-sessions`, share both ways; laptop will be the busy writer later.  
3. **Mint:** `git clone` this repo (or pull if already cloned) so upstairs has the docs/code.  
4. **Desktop:** same clone if you develop there; push/pull via GitHub.  
5. **Matrix:** just join/create a room on the *existing* server from both machines’ clients — optional breadcrumbs only.  
