# Skill: checkpoint

Session-checkpoint: gem alt state til disk i ét kald.

## Trigger

`/checkpoint` eller når Claude vurderer det er tid (efter milestone, før pause, ved vigtig beslutning).

## Hvad den gør

Kør alle trin i rækkefølge:

### 1. Opdatér state-filer
- **CONTEXT.md** — opdatér "Hvor er vi" (seneste session), "Hvad mangler", "Åbne tråde"
- **PROGRESS.md** — append session-narrativ (hvad skete og hvorfor)
- **Projekt-CONTEXT.md** — opdatér relevante projekters CONTEXT.md hvis de blev arbejdet på

### 2. Kør chatlog-engine
```bash
node "c:/Users/Krist/dev/projects/Basic Setup/projects/auto-chatlog/chatlog-engine.js"
```

### 3. Git commit + push
```bash
git add -A && git commit -m "checkpoint: [kort beskrivelse]" && git push
```
Commit-besked skal beskrive *hvad der blev opnået*, ikke "update files".

### 4. Bekræft
Vis kort: hvad blev gemt, hvad er næste step.

## Regler

- Opdatér KUN filer der har reelle ændringer — ingen no-op commits
- CONTEXT.md: kort og præcis. En ny session skal kunne starte ved at læse den.
- PROGRESS.md: narrativt. Hvad *skete* og *hvorfor*.
- Afkryds hvert step med det samme — ikke i batches.

## Hvornår

- Yttre siger `/checkpoint`
- Efter afsluttet step/milestone (Claude foreslår det)
- Før session slutter
- Før compact
