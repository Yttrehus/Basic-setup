# NOW — Hvor vi er

**Sidst opdateret:** 2026-03-10 (session 7)
**Status:** M4 igangværende — step 4 DONE, step 5 næste

## Næste step (start her)

M4 step 5: workspace-fil skabelon for VS Code
Derefter:
- M4 step 6: evaluering af /checkpoint og /new-project skills
- M4 PDCA-evaluering (Check/Act)

## Igangværende

M4 step 4: dotfiles-repo — DONE:
- ~/dev/projects/dotfiles/ oprettet med git + pushed til GitHub (privat, Yttrehus/dotfiles)
- .zshrc stow-symlinket (WSL /home/yttre/.zshrc → dotfiles/zsh/.zshrc)
- .gitconfig kopieret ind i dotfiles/git/
- Scripts flyttet: ~/dev/scripts/ → dotfiles/bin/
- gh CLI installeret og autentificeret (Yttrehus)

Workspace-oprydning:
- Slettet cruft: read-session.js, dump-session.js, session-history.md, chatlog-session4.tmp, habits/
- Oprettet chatlogs/ — dump-chatlog.js + chatlog-YYYY-MM-DD.md samlet her
- dump-chatlog.js omskrevet: grupperer per dato, fletter sessions kronologisk
- PLAN.v1.md + git-concepts.md flyttet til references/
- references/README.md oprettet med indeks over alle filer
- README.md i root opdateret til aktuel struktur

## ~/dev/ konvention (opdateret session 7)

- **projects/** — aktive projekter med eget git repo, CLAUDE.md, PLAN.md, NOW.md
- **projects/dotfiles/** — config-filer + personlige scripts (stow-managed)
- **archive/** — afsluttede/pauserede projekter (read-only reference)
- **sandbox/** — eksperimenter, throwaway kode
- **docs/external/** — tredjeparts-dokumentation
- **BLUEPRINT.md** — historisk reference

## Beslutninger taget (denne session)

- GNU Stow til WSL dotfiles (.zshrc), manuel kopi til Windows (.gitconfig)
- gh CLI installeret (winget) — bruges til GitHub-operationer fremover
- Workspace-struktur: root kun for state-filer + konventionsfiler, alt andet i mapper

## Vigtig kontekst

- Claude Code Bash-tool kører i Windows, ikke WSL
- Windows git konfigureret med SSH — Claude kan commit+push
- gh CLI autentificeret som Yttrehus (HTTPS)
- PostToolUse hook opfanger git commits → minder om NOW.md
- **INGEN session-save hook på PC** — NOW.md skal opdateres manuelt inden session slutter
- Checkpoint-skill sti: chatlogs/dump-chatlog.js (opdateret)

## Åbne tråde

- .editorconfig og .gitattributes mangler i Basic Setup selv
- JetBrains Mono font ikke installeret
- Mermaid Preview extension ikke installeret
- Notion-struktur venter
- Poppler PATH-verifikation efter restart
- Session-management hook til PC (M7-scope)
- vscode.md reference nævner ting der ikke er installeret endnu
- Integrationer parkeret: Gmail, Hotmail, Google (Drev/Calendar/Sheets), mobil-adgang
- 7 parallel task briefs i ~/parallel-tasks/ — klar til Cowork
