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

## Memory Decay

Memories that aren't referenced lose relevance:
- 30+ days without reference → flag stale in `bank/index.md`
- 60+ days → archive to `memory/archive/`
- 90+ days → prune from core memory

**Never decay:**
- Business rules and core facts (bank/world.md)
- Active processes (bank/processes.md)
- High-confidence opinions (>0.7)

**Opinion decay:**
- Low-confidence opinions (<0.3) not updated in 30+ days → remove
- Medium-confidence opinions (0.3-0.7) not updated in 60+ days → reduce confidence by 0.1
- High-confidence opinions (>0.7) → never auto-decay, only demote with contradicting evidence

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