---
name: sitrep
description: Situation report — giver et kompakt overblik over et projekts aktuelle tilstand ved at samle state fra NOW.md, git log, episoder og åbne opgaver.
license: MIT
metadata:
  author: Yttre
  version: "1.0.0"
  domain: workflow
  triggers: sitrep, status, overblik, hvad med nu, giv mig overblik, brief, hvor er vi, hvad mangler, fulde billede, rapport status
  role: analyst
  scope: project
  output-format: briefing
  related-skills: session-resume
---

# Sitrep

Situation report for et projekt eller hele systemet. Samler state fra flere kilder til ét kompakt overblik.

## Hvornår

- "Giv mig overblik" / "hvad med nu?" / "hvor er vi?"
- "Giv mig det fulde billede af..."
- "Hvad mangler?" / "status?"
- Start af arbejdssession (efter session-resume)

## Core Workflow

1. **Identificér scope** — Hvad vil Yttre vide om?
   - a) Specifikt projekt → læs `projects/[projekt]/NOW.md` + `CONTEXT.md`
   - b) Hele systemet → læs alle `projects/*/NOW.md`
   - c) Implicit → udled fra samtale-kontekst

2. **Hent state fra 4 kilder:**
   - **NOW.md** — autoritativ tilstand (hvad er gjort, hvad mangler)
   - **Git log** — `git log --oneline -10` (hvad er faktisk ændret)
   - **Episoder** — `tail -5 data/episodes.jsonl` (seneste sessioner)
   - **Filer** — `ls -lt` på relevante mapper (seneste ændringer)

3. **Syntetisér** — Krydsreferencér kilderne:
   - Er NOW.md opdateret i forhold til git? (drift-check)
   - Er der commits der ikke er reflekteret i NOW.md?
   - Er der episoder der indikerer uafsluttet arbejde?

4. **Præsentér** — Fast format (se template).

## Output Template

```markdown
## Sitrep: [projekt/system]

**Tidspunkt:** [dansk tid]
**Kilde:** NOW.md + git log + episoder

### Tilstand
[2-4 linjer: hvad er gjort, hvad virker, hvad er aktivt]

### Mangler
- [konkrete uafsluttede opgaver, sorteret efter prioritet]

### Drift
[Kun hvis NOW.md og git er ude af sync — ellers udelad denne sektion]

### Næste handling
[1-2 konkrete ting Yttre kan gøre nu]
```

## Constraints

### MUST DO
- Krydsreferencér ALTID mindst 2 kilder (NOW.md + git minimum)
- Vis dansk tidspunkt (TZ=Europe/Copenhagen)
- Vær ærlig om drift — hvis NOW.md lyver, sig det
- Hold output under 25 linjer
- Prioritér "hvad kan gøres NU" over historik

### MUST NOT DO
- Genfortælle hele projektets historie
- Udelade drift-problemer for at se positive ud
- Output uden at have læst NOW.md og git log
- Skrive mere end 30 linjer — det er et sitrep, ikke en rapport
- Foreslå nye projekter eller arkitektur-ændringer — scope er STATUS, ikke planlægning
