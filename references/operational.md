# Operational Reference

## Worker Specialization Tracking

Track which worker configurations (model + tools + prompt style) produce good results in `bank/experience.md`.

**Format:**
```markdown
### Worker Patterns
| Config | Task Type | Success Rate | Notes |
|---|---|---|---|
| model-x + web tools | Market research | 4/5 | Fast, good synthesis |
| model-y + file tools | Content drafting | 3/5 | Needs tone correction |
```

Patterns that work get reused. Patterns that don't get refined. Don't repeat failed configurations.

## Audit Trail

Log significant actions in `memory/YYYY-MM-DD.md` with:
- What was done
- Workers used (if any)
- Cost estimate (if trackable)
- Outcome

**Kanban as audit trail:** For kanban-tracked work, the built-in event stream and comment history serve as the primary audit trail. Use `hermes kanban show <task-id>` to see full history. Use `hermes kanban comment <task-id> "result summary" --author ceo` to record outcomes.

Only duplicate to `memory/YYYY-MM-DD.md` for:
- Cross-task patterns
- Significant decisions spanning multiple tasks
- Errors and recovery attempts

## Opinion Maintenance

Opinions in `bank/opinions.md` should be kept current:
- Low-confidence (<0.3) not updated in 30+ days → remove
- Medium-confidence (0.3-0.7) not updated in 60+ days → reduce confidence by 0.1
- High-confidence (>0.7) → only demote with contradicting evidence

Core business facts (bank/world.md) and high-confidence opinions never auto-decay.

## Daily Log Format

```markdown
# YYYY-MM-DD

## Heartbeat HH:MM
- **Executed**: [task] — [outcome]
- **Created**: [new tasks]
- **Blocked**: [stuck items]
- **Next**: [next action]

## Reflection (if run)
- [Key learnings]
- [Gaps found]
- [What to do differently]
```

Keep entries concise. This is operational logging, not documentation.