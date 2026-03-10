# NOW — Hvor vi er

**Sidst opdateret:** 2026-03-10 (session 8)
**Status:** M4 DONE ✅ — M5 er næste

## Næste step (start her)

M5 step 1: Taskbar og startmenu — hvad skal være der, hvad skal væk
Se PLAN.md for fuld M5-plan (7 steps).

## Hvad sessionen producerede

- **basic-setup.code-workspace** opdateret: extensions-anbefalinger, workspace-settings, opryddet excludes
- **template/project.code-workspace** oprettet: generisk skabelon til nye projekter
- **/new-project skill** aktiveret: opdateret med workspace-fil, flyttet til .claude/skills/
- **M4 PDCA-evaluering** gennemført: /checkpoint virker, /new-project utestet, M4 markeret done

## .claude/ struktur (BS projekt-niveau)

```
.claude/
  skills/              ← instruktioner (hvad)
    checkpoint.md
    session-state.md
    chatlog-search.md
    new-project.md
    infrastructure.md
    notion.md
  implementationlogs/  ← brugsjournal (hvordan det gik)
    checkpoint.md      ← 4 entries, næste evaluering ved #10
    chatlog-search.md  ← 1 entry, evaluering ved #5
```

## Vigtig kontekst

- Claude Code Bash-tool kører i Windows, ikke WSL
- Windows git konfigureret med SSH — Claude kan commit+push
- gh CLI autentificeret som Yttrehus (HTTPS)
- **INGEN session-save hook på PC** — NOW.md skal opdateres manuelt

## Åbne tråde

- JetBrains Mono font ikke installeret
- Mermaid Preview extension ikke installeret
- Notion-struktur venter
- Poppler PATH-verifikation efter restart
- Session-management hook til PC (M7-scope)
- vscode.md reference nævner ting der ikke er installeret endnu
- Integrationer parkeret: Gmail, Hotmail, Google (Drev/Calendar/Sheets), mobil-adgang
- 7 parallel task briefs i ~/parallel-tasks/ — klar til Cowork
- /new-project skill aldrig testet — test ved næste reelle projekt
- Prettier mangler .prettierrc config — kan give uventede formateringer
