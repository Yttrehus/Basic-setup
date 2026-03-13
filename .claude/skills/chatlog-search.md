# Skill: chatlog-search

Find specifik kontekst fra tidligere sessioner. Hvad blev sagt, hvornår, og hvorfor.

## Trigger

Når Yttre eller Claude har brug for at finde en beslutning, diskussion eller kontekst fra en tidligere session. Eksempler:
- "Hvorfor besluttede vi X?"
- "Hvad sagde vi om Y?"
- "Hvornår blev Z implementeret og hvad var tankerne?"

## Hvad den gør

### 1. Søg i chatlog.md
```bash
grep -n -i "<søgeord>" "c:/Users/Krist/dev/projects/Basic Setup/chatlog.md"
```
Brug flere søgeord hvis første søgning er for bred. Kombiner med kontekst (-B/-C flag) for at se omgivende beskeder.

### 2. Find og præsentér
- Vis dato, tidspunkt, og hvem der sagde det (YTTRE/CLAUDE)
- Vis den relevante passage — ikke hele chatloggen
- Hvis beslutningen strækker sig over flere beskeder, sammenfat diskussionen

### 3. Hvis ikke fundet i chatlog
Søg derefter i:
1. PROGRESS.md (narrativ historik)
2. CONTEXT.md (aktuel state, changelog)
3. projects/*/CONTEXT.md (projekt-specifik kontekst)
4. git log (commit-beskeder)

## Regler

- Søg ALTID chatlog.md først, derefter andre kilder
- Vis kun det relevante — aldrig hele filer
- Hvis søgningen tager mere end 3 forsøg, overvej om søgeordene er for generiske
