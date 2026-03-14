# Project Taxonomy

**Dato:** 2026-03-14
**Klar til:** Backlog (design færdigt, kræver implementation + migration)

## Opsummering
Indfør et 7-stage lifecycle-system for projekter i `projects/`. Hver mappe får et præfiks der visuelt viser projektets tilstand i VS Code Explorer. Erstatter den nuværende flade struktur hvor backlog, aktive projekter og afsluttede projekter blandes sammen uden visuel adskillelse.

## Origin Story
Startede i Project Reformation (session 11-13) som en 4-stage pipeline: PoC → DLR → SIP → BMS. Blev droppet i session 13 — det føltes som overengineering da der kun var 3-4 aktive projekter. Terminologien kom fra en Google AI Mode-samtale (arkiveret i `projects/1_archive/architecture.R&D/google-ai-samtale-rd-framework.md`).

I session 17 (2026-03-14, ydrasil-sessionen) dukkede problemet op igen: projekter som `ydrasil`, `manuals` og `auto-chatlog` er "færdige" men bruges aktivt — de passer hverken i backlog eller archive. Det afslørede at der manglede stages for færdige ting der ikke kører som system. Tre nye stages (REF, LIB, KNB) blev designet til at dække dette.

## Problemet
Nuværende mappestruktur:
```
projects/
├── 0_backlog/     ← numerisk præfiks for sortering
├── 1_archive/     ← numerisk præfiks for sortering
├── auto-chatlog/  ← ingen stage-indikation
├── manuals/       ← ingen stage-indikation
├── research/      ← ingen stage-indikation
├── _ydrasil/      ← underscore-hack for sortering
```

Problemer:
1. **Ingen visuel forskel** mellem aktive, færdige og parkerede projekter i Explorer
2. **Inkonsistent sortering** — nummerpræfikser, underscores, plain navne blandet
3. **"Done" er ikke én ting** — chatlog kører automatisk, ydrasil er et arkiv du browser, manuals er kurateret viden. De har brug for forskellige labels
4. **Backlog og archive er pseudo-stages** der bruger mappenavne i stedet for det fælles system

## Løsningen: 7 stages med præfiks

### Pipeline-stages (aktiv udvikling)

| Præfiks | Navn | Betydning | Promotion-kriterier |
|---------|------|-----------|-------------------|
| **PoC** | Proof of Concept | Idé, eksperiment. "Virker det overhovedet?" | Bevist at konceptet holder → DLR |
| **DLR** | Discovery-Led Roadmap | Aktiv research/design. Vejen formes af hvad du finder | Retning valgt, klar til implementation → SIP |
| **SIP** | Staged Implementation Plan | Under opbygning. Bygges kontrolleret ind i systemet | Feature-complete, testet, dokumenteret → BMS/REF/LIB/KNB |

### Done-stages (færdige, i brug)

| Præfiks | Navn | Betydning | Kendetegn |
|---------|------|-----------|-----------|
| **BMS** | Baseline Module System | Kører i systemet, vedligeholdes aktivt | Automatiseret, har hooks/scripts/cron. Fejl skal fikses. |
| **REF** | Reference | Statisk opslagsværk. Du ved hvad du leder efter og slår det op | Faktuelt, ændrer sig sjældent. API-docs, credentials, konfiguration |
| **LIB** | Library | Stor samling du browser i. Du ved ikke altid hvad du leder efter | Mange filer, bredt indhold, søgbart. Research-arkiver, downloaded data |
| **KNB** | Knowledge Base | Kurateret viden bygget til forståelse | Forklarer hvordan ting virker, har visuelle elementer, guides, manuals |

### Specielle mapper (uændret)

| Mappe | Rolle |
|-------|-------|
| `0_backlog/` | Briefs der venter. Ikke en stage — en parkeringsplads for idéer |
| `1_archive/` | Døde projekter. Afsluttet og ikke i brug. Reformation, omdøbning, etc. |

## Navnekonvention

Format: `STAGE.projektnavn`

```
projects/
├── 0_backlog/                  ← uændret
├── 1_archive/                  ← uændret
├── BMS.auto-chatlog/           ← kører automatisk, vedligeholdes
├── DLR.visualisering/          ← under research
├── KNB.manuals/                ← kurateret forståelse, vokser
├── LIB.ydrasil/                ← browsebar samling af VPS-æra data
├── SIP.context-engineering/    ← under implementation
```

### Sortering i Explorer
Præfiks-systemet giver naturlig alfabetisk sortering:
1. `0_backlog` (tal først)
2. `1_archive` (tal først)
3. `BMS.*` (aktive systemer)
4. `DLR.*` (research)
5. `KNB.*` (knowledge bases)
6. `LIB.*` (libraries)
7. `PoC.*` (eksperimenter)
8. `REF.*` (referencer)
9. `SIP.*` (implementation)

### Stage-ændring
Når et projekt skifter stage, omdøbes mappen:
```bash
# Eksempel: manuals går fra SIP til KNB
mv projects/SIP.manuals projects/KNB.manuals
```
CONTEXT.md opdateres med ny stage. Git tracker omdøbningen.

## Regler

1. **Ét præfiks per mappe.** Ingen `SIP.DLR.projekt` — et projekt er i præcis én stage
2. **Præfiks er sandheden.** Hvis CONTEXT.md siger SIP men mappen hedder DLR, er mappen forkert — fix mappen
3. **Demotion er OK.** SIP → DLR når antagelser viser sig forkerte. Ingen skam i at gå tilbage
4. **Done-stages er permanente.** BMS/REF/LIB/KNB skifter sjældent. Hvis de gør, er det et nyt projekt
5. **Backlog-briefs har ingen præfiks.** De er filer i `0_backlog/`, ikke mapper. Præfikser starter når en brief bliver et projekt med egen mappe
6. **Archive er for døde ting.** Ikke for "færdige men brugte" — det er BMS/REF/LIB/KNB

## Forskel mellem REF, LIB og KNB

Disse tre bliver tit forvekslet. Kerneforskel:

| Spørgsmål | REF | LIB | KNB |
|-----------|-----|-----|-----|
| Hvad leder du efter? | Noget specifikt (en API endpoint, en nøgle) | Du browser — "hvad findes der om agents?" | Du vil forstå et emne |
| Ændrer det sig? | Sjældent | Vokser over tid | Kurateres og forbedres |
| Organisering | Flade filer, søgbar | Kategoriseret, indexed | Struktureret, narrativt |
| Eksempel fra Yggdra | API reference, credentials | Ydrasil (91 research + 41 docs + Qdrant) | Manuals (git, terminal, vscode guides) |
| Analogi | Ordbog | Bibliotek | Lærebog |

## Migration

Nuværende → ny navngivning:

| Nu | Bliver til | Begrundelse |
|----|-----------|-------------|
| `auto-chatlog/` | `BMS.auto-chatlog/` | Kører automatisk, vedligeholdes |
| `_ydrasil/` | `LIB.ydrasil/` | Stor samling, browsebar, indexed |
| `manuals/` | `KNB.manuals/` | Kurateret viden, forståelse |
| `research/` | Evaluér: LIB eller merge ind i LIB.ydrasil | Muligt overlap med ydrasil |

Backlog-briefs der aktiveres:
| Brief | Forventet start-stage |
|-------|----------------------|
| context-engineering | SIP (research done, klar til hooks) |
| visualisering | DLR (research-fase) |
| voice-integration | PoC (eksperiment) |
| mcp-skills-kompendium | DLR (research igangsat) |
| integrationer | PoC (umodent) |

## Risici

1. **Omdøbning bryder imports/links** — CONTEXT.md, CLAUDE.md og INDEX.md refererer til mappestier. Alle skal opdateres
2. **Git ser rename som delete+create** — brug `git mv` for at bevare historik
3. **Stage-inflation** — 7 stages er mange. Hvis REF/LIB/KNB aldrig bruges differentieret, kollapser de til ét (fx ARC for "active archive")
4. **Præfiks-fatigue** — hvis det føles som overhead at omdøbe mapper ved stage-skift, er systemet for tungt

## Solnedgangsklausul

**Succes-tegn:** Du kan se i Explorer hvad der er aktivt, hvad der er reference, og hvad der er dødt — uden at åbne filer.
**Kalibrerings-tegn:** REF/LIB/KNB skellet bruges ikke i praksis — kollapser til ét.
**Kill-tegn:** Præfiks-omdøbning skaber mere friktion end det løser. Stage som metadata i CONTEXT.md var nok.
**Evaluering:** Efter 3 aktive projekter har brugt systemet (~4-6 uger).

## Kilder
- `projects/1_archive/architecture.R&D/google-ai-samtale-rd-framework.md` — original PoC/DLR/SIP/BMS design
- `projects/1_archive/architecture.R&D/README-*.md` — stage-dokumenter med promotion/demotion-kriterier
- `projects/1_archive/project-reformation/CONTEXT.md` — hvorfor pipeline-stages blev droppet første gang
- Session 17 (2026-03-14, ydrasil-sessionen) — REF/LIB/KNB designet
