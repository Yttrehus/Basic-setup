# Yggdra

## Metadata
- **Status:** M5 næsten færdig (step 12+15 kræver fysisk adgang). Backlog er næste.
- **Sidst opdateret:** 2026-03-14 (session 15)

## Hvad er det
Personligt udvikler-fundament. Startede som "Basic Setup" (Windows-opsætning), vokset til framework for hvordan Yttre arbejder med AI og kode.

## Hvor er vi

### Seneste session (15 — 2026-03-14)
M5 step 11/13/14/17 gennemført: Downloads ryddet (225→2 filer), .wslconfig oprettet (8GB/4CPU), JetBrains Mono + ligaturer, quick reference. Chatlog-engine token-scanning tilføjet (heuristisk + subagent-verifikation, redact-patterns.json). M6/M7/M8 flyttet fra plan til backlog-briefs. Parallel tasks absorberet i briefs. Backlog-briefs evalueret og opdateret. "Basic Setup" referencer fjernet. architecture.R&D CONTEXT.md oprettet. Google AI samtale flyttet til architecture.R&D. Archive ryddet. Lektie: `rm` i bash bypasser papirkurven.

### Session 14 (2026-03-13)
Chatlog-engine v3: gap-sektioner, subagent-abstracts, danske datoer, secret-redaction. Sessions fra 5 projektmapper samlet i én (~2500 beskeder, 30 sessions). Checkpoint og chatlog-search integreret i auto-chatlog-projektet. Skills audit: forældede stier rettet, checkpoint/chatlog-search forenklet til pointere. Archive ryddet: journals, manuelle chatlogs, dump-scripts slettet (alt i git). Template opdateret: NOW.md+PLAN.md → CONTEXT.md. architecture.R&D fået CONTEXT.md.

### Session 13 (2026-03-13)
Manifest v4 implementeret. Tre iterationer af mappestruktur (pipeline/ → Development/ → projects/) landede på det simpleste: flad projects/-mappe, ét projekt = én mappe. ADR-terminologi og pipeline-stages droppet — erstattet af CONTEXT.md overalt med plain dansk status. Manuals og research ind under projects/. Rod reduceret til 2 mapper (projects/ + .claude/). CONTEXT.md template designet (rekursivt, skalerbart). NOW+PLAN+PROGRESS → CONTEXT.md + PROGRESS.md.

Chatlog v2 krav defineret: én fil (chatlog.md), komplet sessionsdata inkl. tænkeblokke og tool calls, session-baseret inddeling, navigationslinks. Hukommelsesarkitektur skitseret: markdown (nu) → vector DB (snart) → knowledge graph (senere). Claude Memory tilføjet til VS Code workspace.

### Struktur
```
Yggdra/
├── CONTEXT.md, PROGRESS.md, CLAUDE.md, README.md
├── chatlog.md              ← genereret af auto-chatlog engine
├── projects/
│   ├── 0_backlog/          ← 15 idé-briefs (inkl. M6/M7/M8)
│   ├── 1_archive/          ← afsluttede projekter (reformation, omdøbning, architecture.R&D)
│   ├── auto-chatlog/       ← chatlog-engine + checkpoint + chatlog-search
│   ├── manuals/            ← git, vscode, terminal, git-concepts
│   └── research/           ← venter på research-arkitektur
└── .claude/                ← skills, template, settings
```

### Aktive projekter
- **Auto-chatlog:** v3 fungerer (~2500 beskeder, 30 sessions, subagent-abstracts, checkpoint-integration). → `projects/auto-chatlog/CONTEXT.md`

### Afsluttede moduler
- **M1-M3:** Git, VS Code, Terminal (SSH, extensions, WSL, Zsh, Starship)
- **M4:** Projektstruktur (~/dev/ layout, template, /new-project, /checkpoint, dotfiles-repo)

### Venter
- **M5 step 12, 15:** X1 Carbon (BIOS, fysisk adgang), Dev Drive (GUI/admin)

## Hvad mangler
- [x] Reformation ✅
- [x] M5 step 11 — Downloads oprydning (225→2 filer) ✅
- [x] M5 step 13 — .wslconfig (8GB RAM, 4 CPU) ✅
- [x] M5 step 14 — JetBrains Mono + Mermaid Preview ✅
- [x] M5 step 16 — Poppler verificeret ✅
- [x] M5 step 17 — Quick reference ✅
- [ ] M5 step 12 — X1 Carbon (BIOS, Lenovo Vantage, 400 MHz bug — kræver fysisk adgang)
- [ ] M5 step 15 — Dev Drive (evaluer om det giver mening, kræver GUI/admin)
- M6, M7, M8 → backlog-briefs i `projects/0_backlog/`

## Beslutninger

**Rækkefølge:** M5 rest (12, 15 — begge kræver dig) → backlog-projekter efter prioritet

**Metodik:**
- PDCA-cyklus per modul (Plan-Do-Check-Act, Deming)
- Solnedgangsklausul per implementation (succes/kalibrerings/kill-tegn, evalueringstidspunkt)
- Default: justér → omtænk → kill
- Spørg før du bygger. Diskussion færdig → bekræftelse → kode.

**Scope:** Alt der vokser ud over udvikler-fundament bliver separate projekter i `projects/`.

**State-filer:**
- CONTEXT.md (denne fil) — læses automatisk, altid aktuelt overblik
- PROGRESS.md — fuld narrativ, læses efter behov for kontekst
- Hvert projekt har sin egen CONTEXT.md (samme format, rekursivt design)

## Åbne tråde
- Prettier mangler .prettierrc
- /new-project utestet i praksis
- chatlog-search: for tidligt at evaluere

## Changelog
Komprimeret overblik. Fuld detalje i PROGRESS.md.

- **Session 15** (2026-03-14): M5 step 11/13/14/17 done, M6-M8→backlog, token-scanning, parallel tasks absorberet, archive ryddet. → PROGRESS.md#session-15
- **Session 14** (2026-03-13): Chatlog-engine v3, sessions samlet, checkpoint+chatlog-search integreret i auto-chatlog, archive ryddet, template opdateret, reformation fase 6 afsluttet. → PROGRESS.md#session-14
- **Session 13** (2026-03-13): projects/ struktur, ADR→CONTEXT.md, chatlog v2 krav, hukommelsesarkitektur, Claude Memory i workspace. → PROGRESS.md#session-13
- **Session 12** (2026-03-12): Manifest v1-v3 implementeret, 13 briefs, 2 ADR'er retroaktivt. → PROGRESS.md#session-12
- **Session 11** (2026-03-12): Fil-audit, references/ opløst, research-arkitektur identificeret. → PROGRESS.md#session-11
- **Session 10** (2026-03-12): Repo→Yggdra besluttet, M7 trukket ud, CONTEXT.md design, context rot rettet. → PROGRESS.md#session-10
- **Session 9** (2026-03-11): Auto-chatlog prototype, Project Reformation startet, "spørg før du bygger." → PROGRESS.md#session-9
- **Session 8** (2026-03-10): M4 afsluttet, skills evalueret. → PROGRESS.md#session-8
- **Session 7** (2026-03-10): Dotfiles-repo, skills-arkitektur revideret. → PROGRESS.md#session-7
- **Session 6** (2026-03-10): Per-projekt skabelon, /checkpoint og /new-project oprettet. → PROGRESS.md#session-6
- **Session 5** (2026-03-10): ~/dev/ layout, PDCA, solnedgangsklausul, parallel-tasks. → PROGRESS.md#session-5
- **Session 4** (2026-03-10): "Basic Setup er ikke basic", cross-session peer review. → PROGRESS.md#session-4
- **Session 3** (2026-03-10): Session-management problem, VPS research, yggdra-gold. → PROGRESS.md#session-3
- **Session 1-2** (2026-03-08/09): M1-M3 done, PLAN v2, ~/dev/ oprettet. → PROGRESS.md#session-1-2
