# Decisions log

Lightweight ADR-style notes. Newest first.

## 2026-07-09 — Capture conversation into docs

**Context:** Long design conversation: 40-year learning vision, RD-88, Mint host, Pi4, ESP32 LEDs, stereo headcams, Quest curiosity, Twin/Bard naming, corpus, MIDI resolution.

**Decision:** Store as markdown under `docs/`; keep repo product name **Pianissimo**; README title corrected from “Pianisimo.” Prefer **USB-MIDI to Mint** as primary path; DIN optional for MCU/LED sidecar. Quest deferred as Phase 4 display client. Phase 1 = MIDI + screen coach + session memory.

**Alternatives considered:** DIN-first into Pi/ESP; Quest-first UI; vision-first without MIDI.

**Status:** Accepted for planning; revisit when hardware is on the bench.

## 2026-07-09 — Desktop RTX 5070 Ti as GPU annex

**Context:** Desktop GPU (5070 Ti) is up and happy; practice laptop will often be at the keyboard away from the desk.

**Decision:** Keep live loop on Mint; use 5070 Ti for offline reprocess, training, and heavy experiments after Syncthing sync. No dependency on desktop GPU for Phase 1 MIDI+screen.

**Status:** Accepted.

## 2026-07-09 — LAN sync: Syncthing for bits, Matrix for crumbs

**Context:** Practice laptop at the keyboard is distant from the desktop; both on same Wi‑Fi; always-on Matrix server exists; Pianissimo seen as a boba-process learning instant. flowkey felt only “good try”; real-time video + memory is the step up.

**Decision:** Do **not** use Matrix as the session/media sync plane. Use **git** for code/docs, **Syncthing** (or LAN rsync) for library + sessions, **Matrix** for breadcrumbs / Bard-adjacent continuity. Laptop is sole writer during practice.

**Status:** Accepted for planning.

## 2026-07-09 — USB Computer port confirmed via flowkey

**Context:** Owner confirmed one rear USB jack is labeled **Computer**, and it already sent MIDI successfully into a phone running **flowkey**.

**Decision:** Treat that port as the primary Pianissimo input. Phase 0 on Mint is “same cable path as flowkey, different host/app.”

**Status:** Accepted.

## Open questions

- Other rear USB / DIN labels (photo optional)  
- Whether Pi 4 or ESP32 owns LED strip first  
- Library on-disk layout naming when scaffolding starts  
- Whether “Bard” ships as user-visible name or stays internal  
