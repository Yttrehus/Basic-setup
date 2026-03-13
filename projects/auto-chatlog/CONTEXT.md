# Auto-chatlog

## 0. Metadata
- **Status:** I gang — parser fungerer, mangler automatisering og bedre nøgleord
- **Oprettet:** 2026-03-11
- **Sidst opdateret:** 2026-03-13 (session 13)
- **Ejer:** Yttre + Claude

## 1. Origin Story
Auto-chatlog opstod 11/3-2026 under session 9. Yttre observerede at Claude Codes .jsonl sessionsfiler vokser kontinuerligt men aldrig omdannes til læsbar chatlog automatisk. De manuelle chatlog-dumps (dump-chatlog.js + chatlogs/-mappen) krævede at Claude blev bedt om det eksplicit — og outputtet var en flad sekvens uden tidsopdeling eller navigation. Den første prototype blev bygget direkte i session 9, men Claude gik i bygge-mode for tidligt. Yttre kalibrerede: "spørg før du bygger." Tre design-iterationer fulgte: navigationslinks, referater, retskrivning — alt parkeret som fremtidige forbedringer. Format først, automatisering bagefter.

## 2. Current State
chatlog-engine.js v1 fungerer og parser 1000+ beskeder fra 6+ sessions. Producerer to filer: live.md + archive.md (merges til én chatlog.md i v2). Kører manuelt. Kun beskeder — mangler tænkeblokke, tool calls, reasoning. 2-timers tidsblokke som inddeling. Nøgleord er frekvensbaseret og utilstrækkelig.

**V2 krav (session 13):**
- Én fil: chatlog.md (live + archive merged)
- Komplet sessionsdata: beskeder, tænkeblokke, tool calls, reasoning
- Session-baseret inddeling (ikke 2-timers blokke)
- Navigationslinks: prev/next kapitel + hovedindholdsindex
- Bedre indeks (session-baseret, ikke dato-baseret)
- Fremtidig integration med vector DB for semantisk søgning

## 3. Problem Statement
- **Hvad:** Claude Code sessionsfiler (.jsonl) er maskinlæsbare men ikke menneskelæsbare. Der er ingen automatisk omdannelse til chatlog. Manuelle dumps glemmes, og outputtet mangler tidsopdeling og navigation.
- **Hvorfor:** Yttre bruger chatlog som kontekst-kilde mellem sessioner og til retrospektiv ("hvad diskuterede vi?"). Uden læsbar chatlog er man afhængig af hukommelse eller at grave i rå JSONL.

## 4. Target State
Én chatlog.md med komplet sessionsdata (inkl. tænkeblokke og tool calls). Session-baseret inddeling med navigationslinks. Opdateres automatisk. Nøgleord via LLM. Semantisk søgbar via vector DB. Yttre kan finde en specifik diskussion på under 30 sekunder.

## 5. Architecture & Trade-offs
- **Beslutning:** Node.js parser der læser alle .jsonl sessions, splitter på dato (live vs archive), og formaterer som markdown med 2-timers tidsblokke.
- **Brute-force rebuild:** Hele chatloggen rebuildes fra scratch ved hver kørsel. Simpelt, korrekt, men skalerer ikke til hundredvis af sessions. Inkrementel opdatering er fremtidig forbedring.
- **Dansk tid:** UTC konverteres til Europe/Copenhagen. Vigtigt for korrekt datoskift.
- **Truncation:** Beskeder over 5000 tegn afkortes. Balancerer læsbarhed mod fuldstændighed.
- **System-noise filtrering:** <system-reminder>, <ide_*>, <local-command>, <command-name> tags springes over.

## 6. Evaluation
- Kan Yttre finde en specifik diskussion i archive.md under 30 sekunder?
- Kører chatlog-engine.js uden fejl efter 10+ sessions akkumuleret?
- Er live.md nyttig som "hvad lavede vi i dag?"-overblik?
- Erstatter det reelt de manuelle chatlog-dumps?

## 7. Exit Criteria
- **Done:** Kører automatisk (hook eller file-watcher). Nøgleord-extraction er meningsfuld. Brugt friktionsfrit i 5+ sessioner. Gammel chatlogs/-mappe ikke savnet.
- **Demotion:** Fundamental arkitekturfejl (f.eks. JSONL-format ændres og parser bryder).
- **Sunset:** Hvis chatloggen aldrig konsulteres i 10 sessioner, er den cruft.

## 8. Implementation

### Fase 1: Parser-prototype ✅
- [x] chatlog-engine.js — parser .jsonl, splitter live/archive
- [x] Dansk tid (UTC+1)
- [x] 2-timers tidsblokke i archive
- [x] Index-tabel med nøgleord per dato
- [x] Sub-index per tidsblok
- [x] System-noise filtrering
- [x] Truncation af lange beskeder

### Fase 2: Automatisering
- [ ] File-watcher mode (--watch flag, designet men ikke bygget)
- [ ] Eller: PostToolUse hook ved git commit (se projects/backlog/brief.session-drift-pipeline.md)

### Fase 3: Intelligens
- [ ] LLM-baseret nøgleord/referat (lokal LLM, Ollama — se brief i backlog)
- [ ] Navigationslinks mellem tidsblokke
- [ ] Retskrivning af bruger-input
- [ ] Session-ID markering ved parallelle sessions

## 9. Changelog
- 2026-03-11 (session 9, ~09:30): Prototype bygget. 494 beskeder parset. UTC→dansk tid fikset. Kronologisk rækkefølge fikset. 2-timers tidsblokke tilføjet.
- 2026-03-11 (session 9, ~10:00): Nøgleord-extraction testet — frekvensbaseret, utilstrækkelig. LLM-baseret løsning parkeret.
- 2026-03-11 (session 11): Flytning til egen projektmappe. Gammel chatlogs/ pensioneret til archive/.
- 2026-03-12 (session 12): 1098 beskeder fra 6 sessions. Datoskift håndteret korrekt.
- 2026-03-13 (session 13): Strukturændring: projects/auto-chatlog/. ADR → CONTEXT.md. V2 krav defineret: én fil, fuld sessionsdata, session-baseret inddeling, navigationslinks, vector DB integration.

## 10. Backlog
- Navigationslinks mellem tidsblokke
- Lokal LLM til opsummering/nøgleord
- File-watcher eller hook-baseret automatisering
- Inkrementel opdatering (ikke brute-force rebuild)
- Session-ID markering ved parallelle sessions
- Retskrivning af bruger-input

## 11. Original Design
Denne CONTEXT.md er skrevet retroaktivt i session 12 som del af reformation fase 4. Ingen original dokumentation eksisterede — auto-chatlog startede som en ad-hoc prototype i session 9.
