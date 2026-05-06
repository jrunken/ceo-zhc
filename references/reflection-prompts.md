# Reflection Cycle Prompts

Use these as cron job prompts with the Hermes `cronjob` tool.

## Weekly Reflection

Schedule: `0 18 * * 5` (end of Friday)

```
Run weekly reflection for the CEO-ZHC.

1. Read past 7 days of daily logs (~/ceo-workspace/memory/YYYY-MM-DD.md)
2. Write weekly summary → ~/ceo-workspace/memory/weekly/YYYY-WXX.md
 Include: Highlights, Wins, Misses, Patterns Noticed, Next Week Focus
3. Review ~/ceo-workspace/bank/opinions.md — adjust confidence based on week's evidence, remove stale low-confidence items (<0.3, 30+ days)
4. Check entity staleness in ~/ceo-workspace/bank/entities/ — flag items not referenced in 30+ days in bank/index.md
5. Check if ~/ceo-workspace/shared/ files still match reality — update if needed
6. Review worker delegation success rates — update patterns in bank/experience.md
7. Full kanban audit: hermes kanban list → reprioritize, promote triage items, archive completed >2 weeks, check blocked items for escalation
8. Self-critique: "What would I do differently if I started this week over?" Write answer in bank/experience.md
9. Compose weekly investor report and send via send_message:
 - What the company accomplished
 - Key decisions made and why
 - Burn rate / token usage estimate
 - Items stuck (if any)
 - Next week's priorities

Rules: Weekly summaries must be standalone. Be brutally honest about misses. Don't fabricate events.
```

## Monthly Consolidation

Schedule: `0 10 1 * *` (1st of each month)

```
Run monthly consolidation for the CEO-ZHC.

1. Read all weekly summaries from this month
2. Write monthly summary → ~/ceo-workspace/memory/monthly/YYYY-MM.md
 Include: Summary (2-3 paragraphs), Key Achievements, Key Learnings, Opinion Shifts, Entity Changes, Recommendations
3. Archive daily logs older than 60 days → ~/ceo-workspace/memory/archive/YYYY/MM/
4. Deep prune Hermes memory — remove entries no longer relevant
5. Archive entities inactive 90+ days → ~/ceo-workspace/bank/archive/
6. kanban gc: hermes kanban gc — clean archived workspaces, old events, logs. Consider board restructuring.
7. Skill audit: run skills_list, check for skills to create from repeated patterns in bank/experience.md, patch or delete stale skills
8. Compose monthly investor report and send via send_message:
 - Full operational summary
 - Financial summary (if applicable)
 - Strategic direction updates
 - Recommendations for investor consideration

Rules: Monthly summaries are historical record — be comprehensive. Archive, never delete.
```
