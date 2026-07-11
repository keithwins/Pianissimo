# Session schema (draft)

Shapes for Twin memory. Not yet implemented—contracts so recordings do not become anonymous blobs.

## Session

```json
{
  "session_id": "uuid",
  "started_at": "ISO-8601",
  "ended_at": "ISO-8601",
  "host": "mint-i7",
  "instrument": "roland-rd-88",
  "piece_id": "maple-leaf-rag",
  "target_ref": "library/targets/maple-leaf-rag/v1.mid",
  "mode": ["hands-together", "tempo-ladder"],
  "tempo_bpm": 90,
  "notes": "felt rushed in bars 5-8"
}
```

## Streams (files or segments)

| Stream | Format ideas | Clock |
|--------|--------------|-------|
| MIDI performance | `.mid` and/or JSONL note events | host monotonic + UTC |
| Video cam N | `.mkv` / `.mp4` + sidecar index | same host clock |
| Landmarks | JSONL / parquet per frame or per event | frame ts |
| Coach actions | JSONL (highlights, spoken prompts, LED commands) | host clock |
| Twin summaries | JSON metrics for the session | post |

### Note event (JSONL sketch)

```json
{
  "t_ms": 12345,
  "type": "note_on",
  "note": 60,
  "velocity": 87,
  "channel": 0
}
```

## Twin aggregates (per piece / over time)

Examples—not exhaustive:

- Onset error histogram vs target  
- Velocity profiles by finger/region (when fingering known)  
- Bars with repeated failure; drills that followed; outcome next session  
- Tempo ladder progress  

## Privacy

Sessions local by default. Export / cloud Bard only with explicit action.
