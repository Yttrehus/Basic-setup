---
name: dialectic-pipeline
description: Struktureret adversarial evaluering af en ide, beslutning eller arkitektur. Bruger steelman/red-team dynamik til at finde blinde pletter og styrke argumenter.
license: MIT
metadata:
  author: Yttre
  version: "1.0.0"
  domain: analysis
  triggers: dialectic, adversarial, steelman, red team, djævlens advokat, stress-test, udfordr dette, prik huller, neutral evaluering
  role: adversarial-analyst
  scope: decision
  output-format: structured-verdict
  related-skills: sitrep
  origin: chatlog 14/3-2026, session med Socratisk udfordring af Ydrasil-systemet
---

# Dialectic Pipeline

Struktureret adversarial proces der tester en ide fra flere vinkler. Inspireret af Socratisk metode og formaliseret red-teaming.

## Hvornaar

- Yttre vil stress-teste en beslutning eller arkitektur
- "Udfordr dette" / "prik huller" / "steelman dette"
- Foer vigtige beslutninger (ny service, ny integration, design-valg)
- Naar en ide foeles for god til at vaere sand

## Modes

### 3-step (hurtig)
Brug naar scope er smaalt eller tid er knap.

1. **Propose** — Formuler ideen klart som en thesis (3-5 saetninger)
2. **Red Team** — Angrib thesis. Find 3-5 svagheder, blinde pletter, risici. Vaer brutal
3. **Verdict** — Syntese: hvad holder, hvad holder ikke, hvad mangler data

### 5-step (fuld)
Brug naar beslutningen er vigtig eller konsekvensrig.

1. **Propose** — Formuler thesis (3-5 saetninger)
2. **Steelman** — Staerk thesis saa meget som muligt. Find de bedste argumenter FOR. Antag god tro
3. **Red Team (The Fool)** — Angrib den steelmanned thesis. Rollen: "The Fool" — ingen hellige koeer, ingen hoeflighedsfiltre. Find 3-5 fatale svagheder
4. **Steelman Red Team** — Tag red-team's bedste pointer og staerk DEM. Hvad hvis kritikken har ret?
5. **Neutral Evaluator** — Upartisk syntese. Vejer begge sider. Output: verdict med confidence

## Core Workflow

1. **Identificer thesis** — Hvad evaluerer vi? Kilde: Yttres input, en CONTEXT.md, en beslutning
2. **Vaelg mode** — 3-step (default) eller 5-step (hvis Yttre beder om fuld eller emnet er komplekst)
3. **Koer pipeline** — Hvert step producerer tekst. Steps kan koeres som subagents (parallel: steelman + red-team)
4. **Output verdict** — Struktureret resultat (se template)

## Output Template

### 3-step

```markdown
## Dialectic: [emne]

### Thesis
[3-5 saetninger]

### Red Team
1. [svaghed/risiko]
2. [svaghed/risiko]
3. [svaghed/risiko]

### Verdict
**Holder:** [hvad der overlever kritik]
**Svagt:** [hvad der ikke holder]
**Mangler:** [hvad vi ikke ved]
**Anbefaling:** [konkret handling]
```

### 5-step

```markdown
## Dialectic: [emne]

### Thesis
[3-5 saetninger]

### Steelman
[Bedste argumenter FOR thesis. 3-5 punkter]

### Red Team (The Fool)
[Brutalt angreb paa steelmanned thesis. 3-5 fatale svagheder]

### Steelman Red Team
[Red team's bedste pointer styrket. 2-3 punkter]

### Neutral Evaluator
**For-argumenter der holder:** [liste]
**Kritik der holder:** [liste]
**Confidence:** [hoej/middel/lav]
**Verdict:** [1-2 saetninger]
**Anbefaling:** [konkret naeste skridt]
```

## Constraints

### MUST DO
- Vaer AERLIG. Hverken smiger eller destruktion. Sandhed
- Red Team SKAL vaere brutal — ingen hoeflighedsfiltre. "The Fool" har licens til at sige alt
- Steelman SKAL vaere i god tro — find de BEDSTE argumenter, ikke straamand
- Neutral Evaluator SKAL vaere upartisk — veej begge sider reelt
- Citer konkret evidens naar muligt (filer, data, erfaringer)
- Hold hvert step under 10 linjer — kompakt, ikke essay
- Angiv confidence i verdict (hoej/middel/lav)

### MUST NOT DO
- Vaere hoeflig i Red Team — det oedelaegger formaalet
- Vaere destruktiv i Steelman — det oedelaegger formaalet
- Lade bias fra et step laekke ind i naeste
- Skrive mere end 40 linjer total (3-step) eller 60 linjer (5-step)
- Koere 5-step naar 3-step er nok — respekter Yttres tid
- Bruge dialectic paa trivielle beslutninger (valg af filnavn etc.)

### KILL CONDITION
Fjern dette skill hvis det ikke bruges inden 3 maaneder efter oprettelse (14/6-2026).
