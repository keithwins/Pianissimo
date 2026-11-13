# Next update

Things agreed but not built yet. Remove each once it's done.

- **Key colors too faint (Keith, 261113).** Keys marking notes about to be played are tinted with only 32% of the hand colour on white keys (`.wk.hint-r` / `.wk.hint-l`, `color-mix … 32%`), which washes out on his screen. Add a "Key colors" strength slider under Settings, Show (from the faint tint to full colour; raise the default), and right- and left-hand colour pickers that recolour keys, falling notes and staff marks together (stored as overrides of `--rh` / `--lh`; the first piece of colour skins).

## Offered, not decided

- Library safeguards: pin the three outside libraries (bundle them, or integrity hashes) and size caps on imported files (from the trojan question, 261112).
- Landmarks with key signatures: same positions, the key changes what they mean (F line in D major is F♯), a key at a time.
- Reading aids for the staff: larger staff, fewer bars at a time, tinted landmark lines, wider note spacing, note names that fade.
