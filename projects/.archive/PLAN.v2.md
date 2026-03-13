# Basic Setup — Plan v2

**Mål:** Professionelt udviklermiljø på Windows 11 med WSL, VS Code, Git og god struktur.
**Tilgang:** Yttre gør det selv — Claude guider. Steps kort først → ét ad gangen.
**Metode:** Byg → Evaluér → Notér → Parkér idéer (PDCA-cyklus per modul).

---

## Afsluttede moduler

### M1: Git ✅
### M2: VS Code ✅
### M3: Terminal/Shell ✅

Detaljer i projects/archive/PLAN.v1.md.

---

## M4: Projekt-struktur ✅

**Formål:** Organisér ~/dev/ så projekter har konsistent struktur og config-filer er versioneret.

1. [x] Research: hvad gør professionelle? Mappestruktur, konventioner
2. [x] ~/dev/ layout og konventioner — fastlagt session 5, tools/ slettet, scripts/→dotfiles/bin/ planlagt
3. [x] Standard per-projekt skabelon (CLAUDE.md, PLAN.md, NOW.md, .gitignore, .editorconfig, .gitattributes)
4. [x] Dotfiles-repo — versionér .zshrc, .gitconfig, starship.toml + flyt ~/dev/scripts/ → dotfiles/bin/ (på PATH)
5. [x] Workspace-fil skabelon for VS Code
6. [x] Evaluering: /checkpoint skill + /new-project skill — virker de? Justér baseret på brug i step 3-5.

**Done-kriterie:** Nyt projekt kan startes med `/new-project` og have al infrastruktur klar. /checkpoint bruges friktionsfrit.

**PDCA-evaluering (session 8):**
- /checkpoint: virker friktionsfrit fra brug #3. Tidlige fejl var setup-problemer (CRLF, chatlog-sti), ikke design. Behold uændret, næste evaluering ved brug #10.
- /new-project: skabelon komplet (7 filer), skill aktiv, men utestet. Test ved næste reelle projekt, evaluér efter 2 brug.
- chatlog-search: 1 test-brug, for tidligt at evaluere. Evaluér efter 5 brug.
- Done-kriterie: opfyldt med forbehold — /new-project aldrig testet i praksis.

---

## M5: PC-setup (Windows) — I GANG

**Formål:** Windows konfigureret som en professionels arbejdsstation. Fuldt professionelt.

1. [x] Research: professionelle dev setups, X1 Carbon Gen 13, privacy, creators (Hanselman, Janetakis, ThePrimeagen)
2. [x] PowerToys — installeret + konfigureret: FancyZones, Command Palette, Peek, File Locksmith
3. [x] Privacy-hardening — Settings UI (4 steder), Group Policy (Pro), DiagTrack service, notifications
4. [x] Taskbar + startmenu — clutter fjernet, daglige apps pinned, left-aligned
5. [x] Windows settings — Developer Mode, File Explorer (vis extensions), clipboard history, default terminal, End Task
6. [x] Tema + display — dark mode, accent color, scaling (100% på 1920x1200), Night Light
7. [x] Input — touchpad gestures, mus-acceleration, scroll gennemgået
8. [x] Default apps + lyd — browser sat, filassociationer gennemgået
9. [x] Power settings — timeouts, lid close, OneDrive kontrol gennemgået
10. [x] Software-audit — 7-Zip + Everything installeret, 11 bloatware-apps fjernet
11. [ ] Filsystem — C:\Users\Krist organiseret, Downloads oprydning, Desktop ryddet
12. [ ] X1 Carbon specifikt — BIOS-check (VT-x/VT-d), Lenovo Vantage (battery threshold 80%), 400 MHz bug check
13. [ ] .wslconfig — sæt RAM/CPU-grænser for WSL2
14. [ ] Fonts + extensions — JetBrains Mono, Mermaid Preview
15. [ ] Dev Drive — evaluer om det giver mening (kræver 50GB+, flyt ~/dev/)
16. [ ] Poppler PATH-verifikation (installeret, mangler restart)
17. [ ] Quick reference — PowerToys genveje, Windows shortcuts, touchpad gestures (én reference-fil til daglig brug)

**Done-kriterie:** Skrivebord, taskbar og filsystem organiseret. Privacy hardened. PowerToys konfigureret. Alle tools installeret. Reference-filer opdateret.

**Research-filer:** projects/research/archive/windows-setup-research.md, projects/research/archive/x1-carbon-gen13-dev-setup.md

---

## M6: Terminal-automatisering

**Formål:** VS Code åbner med de terminaler du bruger dagligt.

1. [ ] Definér terminaler per workspace (WSL, SSH VPS, claude)
2. [ ] .vscode/tasks.json med runOn: folderOpen
3. [ ] Test og tilpas

**Done-kriterie:** Åbn workspace → terminaler klar.

---

## M7: Context engineering

Trukket ud som selvstændigt projekt. Se `projects/backlog/brief.context-engineering.md`.

---

## M8: Skabeloner til nye projekter

**Formål:** Nye projekter starter med det fundament vi har bygget. Syntese af alt.

1. [ ] Projekt-skabelon (CONTEXT.md, CLAUDE.md, .gitignore, workspace-fil)
2. [ ] Checkliste for nyt projekt
3. [ ] Reference-samling
4. [ ] Scope-definition template (hvad er projektet, hvad er det IKKE)

**Done-kriterie:** Nyt projekt på under 5 minutter med al infrastruktur klar.

---

## PDCA-cyklus (per modul)

Plan-Do-Check-Act (Deming). Vores version:

1. **Plan** — definér steps + done-kriterie
2. **Do** — gennemfør steps
3. **Check** — opfyldte vi done-kriteriet? Hvad overraskede?
4. **Act** — notér retrospektiv, parkér nye idéer, justér planen

## Solnedgangsklausul (per ny implementation)

Hver ny implementation definerer *før* den bygges:
- **Succes-tegn:** Hvad ser vi hvis det virker perfekt?
- **Kalibrerings-tegn:** Hvad ser vi hvis det skal justeres?
- **Kill-tegn:** Hvad ser vi hvis det skal fjernes?
- **Evalueringstidspunkt:** Hvornår tjekker vi?

Default-respons ved uventet adfærd: **justér → omtænk → kill** (i den rækkefølge).

---

## Idé-parkering → projects/backlog/

Alle idéer er nu briefs i `projects/backlog/`. Se brief-filer der. Migreret i session 12 (reformation fase 3).

Ikke-migreret: Adobe Acrobat Pro (for tynd til brief — tilføjes ved behov).

---

## Scope-grænse

Basic Setup er opsætning af professionelt udviklermiljø. Alt der vokser ud over dette bliver separate projekter i `projects/`.

---

## Rækkefølge

Reformation done → M5 (færdiggør) → M6 → M7/CE → M8

**Project Reformation status:** Fase 5 i gang (CONTEXT.md). Se `projects/project-reformation/CONTEXT.md`.
