# NOW — Hvor vi er

**Sidst opdateret:** 2026-03-10 (session 3+4 aktive)
**Status:** M4 igangværende — step 1 research DONE, step 2 ~/dev/ layout 90% done

## Næste step (start her)

M4 step 2 afsluttes: fastlæg konventionen for ~/dev/ layout (sandbox/, tools/ er bekræftet intentionelle). Derefter:
- M4 step 3: per-projekt skabelon (.editorconfig, .gitattributes, CLAUDE.md, PLAN.md, NOW.md, .gitignore)
- M4 step 4: dotfiles-repo
- M4 step 5: workspace-fil skabelon

## Igangværende

M4 step 2: ~/dev/ layout — mapper er flyttet:
- `dev/projects/Basic Setup/` ✓
- `dev/archive/Old stuff/` ✓
- `dev/archive/research archive/` ✓
- `dev/scripts/` ✓ (ctx, tunnel, setup — Yggdra PC-tools, flyttet fra ~/)
- `dev/docs/` ✓ (external LLM docs, flyttet fra ~/)
- `dev/BLUEPRINT.md` ✓ (historisk reference, flyttet fra ~/)
- `dev/sandbox/` — tom, til eksperimenter (oprettet forrige session)
- `dev/tools/` — tom, til CLI-værktøjer (oprettet forrige session)

Mangler: fastlæg konventionen (hvad hører hvor), evt. README i ~/dev/

## Beslutninger taget (denne session)

- Basic Setup er main workspace. Sub-projekter vokser ud herfra til egne workspaces.
- M7 (context engineering) bekræftet som research-projekt — rækkefølgen M4→M5→M6→M7 holdes.
- BLUEPRINT.md er historisk dokument, opdateres ikke løbende.
- PC'ens ~/dev/ skal tage principper fra VPS (state på disk, progressive disclosure, CONTEXT.md + NOW.md per projekt) men IKKE kopiere VPS-strukturen ukritisk — VPS har cruft.
- Yggdras save_checkpoint.py/load_checkpoint.sh undersøgt som reference for M7.

## Hvad sessionen producerede

- `references/project-structure.md` — research om professionelle mappestruktur-konventioner (7 sektioner, 25+ kilder)
- `references/yggdra-gold.md` — destillerede guldkorn fra VPS docs/research/dagbog (8 kategorier med kildehenvisninger)
- `chatlog-2026-03-10.md` — fuld chatlog (76 beskeder)
- Gennemgik ALLE filer i Basic Setup (22 filer) + VPS docs/ (40+ filer) + archive
- Opdateret memory-fil i ~/.claude/projects/

## Seneste sessioner

### 2026-03-10 (denne)
- Mapper flyttet: scripts/, docs/, BLUEPRINT.md → dev/
- Session-hukommelse-problem identificeret og diskuteret grundigt
- Undersøgte Yggdra hooks: save_checkpoint.py, load_checkpoint.sh, episodes.jsonl
- Deep dive i VPS: DAGBOG, YDRASIL_ATLAS, HANDLINGSPLAN, PC_SETUP, PAI_BLUEPRINT, ARCHITECTURE_CONTINUOUS_MEMORY, MANUAL, PRIORITIES, TRADEOFFS, MISSION
- Research om professionelle mappestruktur-konventioner (web + mcpmarket)
- Gennemgik alle filer i Basic Setup — identificerede outdated/manglende filer
- Yttre frustreret over tabt kontekst fra forrige session → chatlog gemt for fremtiden

### 2026-03-09
- M3 gennemført: Zsh + Oh My Zsh + Starship + plugins + aliases
- V2 plan designet og implementeret (PLAN.md v2, references/, Popper-loop)
- M4 research påbegyndt: scannede mcpmarket.com, parkerede idéer
- Poppler installeret, research (GSD, RPI, PRD-first, AI-biografi)
- ~/dev/ oprettet med projects/, archive/, sandbox/, tools/

## Vigtig kontekst

- Claude Code Bash-tool kører i Windows, ikke WSL
- Windows git konfigureret med SSH — Claude kan commit+push
- PostToolUse hook opfanger git commits → minder om NOW.md
- **INGEN session-save hook på PC** — NOW.md skal opdateres manuelt inden session slutter
- Yggdra (VPS) har fuldt hook-system — reference i references/yggdra-gold.md

## Åbne tråde

- JetBrains Mono font ikke installeret
- Mermaid Preview extension ikke installeret
- Notion-struktur venter
- Poppler PATH-verifikation efter restart
- Session-management hook til PC (M7-scope)
- habits/ mappe er tom — intention ukendt fra forrige session
- .editorconfig og .gitattributes mangler (identificeret i research)
- vscode.md reference nævner ting der ikke er installeret endnu
