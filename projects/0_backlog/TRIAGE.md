# Triage — Prioriteret overblik

Sidst opdateret: 2026-03-14

## Klar (research done, kan startes)

| Brief | Modenhed | Blokerer | Noter |
|-------|----------|----------|-------|
| context-engineering | spec'd | research-architecture (delvist) | Research udført (8 kilder). Hooks fase 1-2 done. Fase 3-5 venter |
| automation-index | brief | — | Quick win: index eksisterende hooks/cron/workflows |
| research-architecture | spec'd | — | VPS audit done. INDEX.md v3 med 54 Key Insights hentet. Fase 2+ venter |

## Næste op (kræver lidt forberedelse)

| Brief | Modenhed | Blokeret af | Mangler |
|-------|----------|-------------|---------|
| notion-spejling | brief | notion MCP | Notion-database + test af mobiltilgang |
| pdf-skill | brief | — | Faktura-layout fra rejseselskab, weasyprint, Tesseract |
| abonnement-overblik | brief | — | PureGym/United Fitness, daglige udgifter, årsopgørelse 2025 |
| cross-session-peer-review | brief | — | Design for parallel session workflow |

## Kræver skærpning (scope uklart)

| Brief | Modenhed | Hvad mangler |
|-------|----------|--------------|
| integrationer | sketch | Gmail MCP done. GDrive/Calendar/Sheets scope uafklaret |
| visualisering | sketch | Scope-valg: data-viz, diagrammer, layout, eller præsentation? |
| voice-integration | sketch | Tre retninger — skal vælge én |

## Lav prioritet / parkeret

| Brief | Modenhed | One-liner |
|-------|----------|-----------|
| project-taxonomy | brief | 7-stage lifecycle præfiks. Design færdigt, kræver migration |
| work-intake | brief | Denne fil ER deliverable. Meta-brief |

## Afhængigheder

```
research-architecture ──→ context-engineering (INDEX.md som input)
notion MCP ──→ notion-spejling
faktura-layout ──→ pdf-skill
```

## Session-forslag

Baseret på modenhed + prioritet:
1. **context-engineering fase 3-5** — mest modent, størst impact på dagligt arbejde
2. **automation-index** — quick win, 1-2 timer, giver overblik over hvad der kører
3. **research-architecture fase 2** — bygger videre på v3 INDEX.md der lige er hentet
