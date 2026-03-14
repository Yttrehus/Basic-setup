---
name: session-resume
description: Resume a session or coordinate between parallel sessions. Reads checkpoints, episodes, and parallel session state to restore context fast.
license: MIT
metadata:
  author: Yttre
  version: "1.0.0"
  domain: workflow
  triggers: resume, session resume, hvad skete der, genoptag, fortsæt session, session koordinering, list sessions, hvad laver de andre sessions, session id
  role: coordinator
  scope: session
  output-format: briefing
  related-skills: sitrep
---

# Session Resume

Genskaber kontekst fra en tidligere eller parallel session. Samler checkpoint-data, episoder og parallel session state til en kompakt briefing der gør det muligt at fortsætte arbejdet uden konteksttab.

## Hvornår

- Start af ny session ("hvad skete der sidst?")
- Skift mellem parallelle sessions ("hvad laver de andre?")
- Efter compaction ("genoptag kontekst")
- Når Yttre spørger "hvad er session id?" eller "list sessions"

## Core Workflow

1. **Identificér kontekst** — Hvad beder Yttre om?
   - a) Genoptag seneste session → læs checkpoint + episoder
   - b) Koordinér parallelle sessions → læs alle aktive checkpoints
   - c) Find specifik session → søg i checkpoint-filer/episoder

2. **Hent data** — Afhængigt af kontekst:
   - Checkpoint: `data/checkpoints/` eller `.claude/.compact_marker`
   - Episoder: `data/episodes.jsonl` (seneste 5)
   - Parallel sessions: `data/SESSION_RESUME.md`
   - Git: `git log --oneline -5`

3. **Syntetisér** — Byg en kompakt briefing:
   - Hvad blev gjort (seneste session/iteration)
   - Hvad er åbent (uafsluttede opgaver)
   - Hvad er næste skridt
   - Parallelle sessions (hvis relevant)

4. **Præsentér** — Output i fast format (se template).

## Output Template

```markdown
## Session Resume

**Seneste session:** [timestamp] ([session-id])
**Projekt:** [aktivt projekt]
**Seneste commit:** [git log --oneline -1]

### Hvad skete
- [1-3 bullet points fra checkpoint/episoder]

### Åbent
- [uafsluttede opgaver, blokkere]

### Næste skridt
- [1-2 konkrete handlinger]

### Parallelle sessions (hvis aktive)
| Session | Projekt | Status |
|---------|---------|--------|
| [id]    | [proj]  | [kort] |
```

## Constraints

### MUST DO
- Læs ALTID checkpoint-data FØR du svarer — gæt ikke på kontekst
- Hold briefingen under 20 linjer — kompakt, ikke udtømmende
- Inkludér session-id og tidspunkt
- Vis git log (seneste commit) som ground truth
- Ved parallel-koordinering: vis ALLE aktive sessions

### MUST NOT DO
- Genfortælle hele session-historikken — kun highlights
- Gætte på hvad der skete uden at læse data
- Ignorere parallelle sessions når de eksisterer
- Output mere end 30 linjer — det er en briefing, ikke en rapport
