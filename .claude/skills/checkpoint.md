# Skill: checkpoint

Session-checkpoint. Se `projects/auto-chatlog/CONTEXT.md` for fuld dokumentation.

## Trigger
`/checkpoint` eller ved milestone/pause/vigtig beslutning.

## Trin
1. Kør chatlog-engine: `node projects/auto-chatlog/chatlog-engine.js --digest` → spawn subagent (haiku, abstracts) → `node projects/auto-chatlog/chatlog-engine.js`
2. Opdatér CONTEXT.md + PROGRESS.md + relevante projekt-CONTEXT.md
3. Git commit + push
4. Bekræft kort
