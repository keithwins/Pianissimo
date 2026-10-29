# Pianissimo

A piano practice player that runs in the browser (Chrome). Open a MusicXML score, connect a MIDI keyboard, and practise with a staff, falling notes, fingering, sections, simple games and a harmony strip.

Your scores, fingering and practice records stay in a folder on your own computer. Nothing is uploaded.

The library can be searched and filtered by composer, era, key, meter, tempo and your own tags (kept in each piece's sidecar file). Pianissimo suggests tags from what it sees in the notes; you keep or dismiss them. The library also holds generated exercises (scales, arpeggios and patterns in any key, plus five-finger patterns) that play like any piece. A section of a piece can be turned into a matching drill, and Wait for me can listen through the microphone when there is no MIDI keyboard. See `docs/` for the design notes.

**Use it:** https://keithwins.github.io/pianissimo/ (once Pages is switched on)

Requires Chrome (or another Chromium browser) for keyboard and folder access.

## Privacy

Nothing you play, record or store leaves your computer. There is no server, no account and no analytics. Fonts are bundled in the page. The page loads three code libraries from public CDNs (see THIRD_PARTY.md).

## Scores

The starter pieces are public-domain compositions with notes-only encodings. Details and credits are in [THIRD_PARTY.md](THIRD_PARTY.md). If you contribute a score, it must be public domain or openly licensed, with its source noted.

## License

MIT, see [LICENSE](LICENSE).
