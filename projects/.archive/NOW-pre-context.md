# NOW — Hvor vi er

**Sidst opdateret:** 2026-03-13 ~01:00 (session 13)
**Status:** Project Reformation — fase 5 i gang. Rod-CONTEXT.md udkast lavet, template diskuteret.

## Næste step (start her)

**Denne session:** Fase 5 — CONTEXT.md.
1. [x] Manifest v4 implementeret (projects/ struktur)
2. [x] Alle projekt-CONTEXT.md-filer opdateret (pipeline/ → projects/, plain dansk status)
3. [x] CONTEXT.md template diskuteret og udkast lavet
4. [ ] Finalisér rod-CONTEXT.md
5. [ ] Arkivér PLAN.md → `projects/archive/PLAN.v2.md`
6. [ ] Arkivér PROGRESS.md → `projects/archive/PROGRESS.md`
7. [ ] Slet NOW.md og PROGRESS.md
8. [ ] Opdatér CLAUDE.md: `@NOW.md` → `@CONTEXT.md`
9. [ ] Commit + push

## Hvad session 13 producerede

### Strukturændring (manifest v4)
- `pipeline/` → `projects/` (flad, ét projekt = én mappe)
- ADR-filer → CONTEXT.md (rekursivt design, samme format overalt)
- `manuals/` og `research/` ind under `projects/`
- Governance READMEs og stage-mapper droppet
- Rod reduceret til 2 mapper (projects, .claude)

### CONTEXT.md design
- Template: Metadata, Hvad er det, Hvor er vi, Hvad mangler, Beslutninger, Changelog
- Status i plain dansk ("I gang — parser fungerer, mangler automatisering")
- Graduated summary i changelog (seneste session fuld detalje, ældre progressivt komprimeret)
- Skalering: brief = kun Metadata + Hvad er det. Komplekst projekt = alle sektioner.

### Beslutninger
- Ét format: CONTEXT.md overalt — rod og projekter
- Stage er metadata, ikke mappestruktur
- Pipeline-terminologi (PoC/DLR/SIP/BMS) droppet
- `projects/` i roden (konsistent med VPS)
- Tre state-filer → én CONTEXT.md

## Åbne tråde

- M5 step 11-17 (filsystem, X1, fonts, Dev Drive, wslconfig, quick reference)
- Checkpoint-skill: skal opdateres til CONTEXT-check
- Poppler PATH-verifikation efter restart
- Prettier mangler .prettierrc
- /new-project utestet i praksis
