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
- Scripts flyttet: ~/dev/scripts/ → dotfiles/bin/ (ctx, tunnel, notion, setup, get_context.py, notion_api.py)
- PATH opdateret i .zshrc til dotfiles/bin/
- ~/dev/scripts/ slettet
- GNU Stow installeret i WSL
- gh CLI installeret og autentificeret (Yttrehus)
- README.md med stow-instruktion

## ~/dev/ konvention (opdateret session 7)

- **projects/** — aktive projekter med eget git repo, CLAUDE.md, PLAN.md, NOW.md
- **projects/dotfiles/** — config-filer + personlige scripts (stow-managed)
- **archive/** — afsluttede/pauserede projekter (read-only reference)
- **sandbox/** — eksperimenter, throwaway kode (ingen forventning om at overleve)
- **docs/external/** — tredjeparts-dokumentation
- **BLUEPRINT.md** — historisk reference

## Beslutninger taget (denne session)

- GNU Stow til WSL dotfiles (.zshrc), manuel kopi til Windows (.gitconfig)
- gh CLI installeret (winget) — bruges til GitHub-operationer fremover
- ~/dev/scripts/ slettet efter flytning til dotfiles/bin/

## Vigtig kontekst

- Claude Code Bash-tool kører i Windows, ikke WSL
- Windows git konfigureret med SSH — Claude kan commit+push
- gh CLI autentificeret som Yttrehus (HTTPS)
- PostToolUse hook opfanger git commits → minder om NOW.md
- **INGEN session-save hook på PC** — NOW.md skal opdateres manuelt inden session slutter

## Åbne tråde

- JetBrains Mono font ikke installeret
- Mermaid Preview extension ikke installeret
- Notion-struktur venter
- Poppler PATH-verifikation efter restart
- Session-management hook til PC (M7-scope)
- habits/ mappe er tom — intention ukendt fra forrige session
- .editorconfig og .gitattributes mangler i Basic Setup selv (template har dem, BS endnu ikke)
- vscode.md reference nævner ting der ikke er installeret endnu
- Integrationer parkeret: Gmail, Hotmail, Google (Drev/Calendar/Sheets), mobil-adgang
- 7 parallel task briefs i ~/parallel-tasks/ — klar til Cowork
