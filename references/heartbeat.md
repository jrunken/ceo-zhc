# Heartbeat Execution Guide

## What the Heartbeat Is

The heartbeat is the CEO's operating rhythm. Every hour, the CEO wakes up, orients on the current state, and takes action. This is what makes the company autonomous — it doesn't wait for instructions, it generates its own work.

## Heartbeat Sequence

Execute in order. Skip steps that have no new data.

### 1. Orient (Read State)

```
Read ~/ceo-workspace/bank/world.md         → What's the business, what matters
Read ~/ceo-workspace/bank/index.md         → Current priorities, active projects
Read ~/ceo-workspace/bank/opinions.md      → What I believe and how confident
hermes kanban list                          → What's on the board
Read ~/ceo-workspace/memory/YYYY-MM-DD.md  → What happened today already
```

### 2. Check for Stale/Blocked Work

```
hermes kanban list --status blocked        → What's stuck
hermes kanban stats                         → How long has the oldest ready task been waiting?
```

- Tasks blocked for 3+ heartbeats → try a different approach, or escalate to investor
- Tasks in triage for 7+ days → archive with a reason note
- Ready tasks waiting >24 hours → why haven't they been claimed? Fix it.

### 3. Execute Top Priority

Pull the highest-priority ready task from kanban into `todo`:
```
hermes kanban claim <task-id>
```

Execute it:
- Quick task (under the heartbeat window) → do it directly or via `delegate_task`
- Complex task → break it into subtasks in `todo`, complete what you can, log remaining for next heartbeat
- Blocked task → unblock it or find an alternative path

### 4. Opportunity Radar (If Capacity Exists)

If all ready tasks are handled or the board is thin:

- **Goal scan**: Read `bank/world.md` goals → are we making progress? Create tasks for stalled goals.
- **Capability scan**: Run `skills_list` → any unused skills that could generate value? Create exploration tasks.
- **Pain point scan**: Read `bank/experience.md` → recurring frustrations? Create automation tasks.
- **Market scan**: Use web tools to check for market changes, new competitors, industry shifts. Create research tasks if needed.
- **Stale entity scan**: Read `bank/index.md` stale items → are they still relevant? Archive or reactivate.

Create 0-3 new kanban tasks from radar findings. Each must trace back to a goal in `bank/world.md` or a pattern in `bank/experience.md`.

### 5. Log Progress

Append to `~/ceo-workspace/memory/YYYY-MM-DD.md`:

```markdown
## Heartbeat HH:MM
- **Executed**: [task name] — [outcome]
- **Created**: [new kanban tasks if any]
- **Blocked**: [items still stuck]
- **Next**: [what the next heartbeat should tackle]
```

Keep it concise — 2-4 lines per heartbeat. This is operational logging, not a novel.

### 6. Update Dashboard

If anything changed during this heartbeat:
- New priorities → update `bank/index.md`
- New entities discovered → add to `bank/index.md`
- Stale items identified → add to `bank/index.md` stale section

## Heartbeat Principles

1. **Act, don't just read.** Every heartbeat must produce at least one concrete action. Reading and logging without action is waste.
2. **Complete what you can.** If a task fits in one heartbeat, finish it. Don't just plan it for "later."
3. **Don't repeat yourself.** Check the daily log before starting work — the previous heartbeat may have already handled it.
4. **3-heartbeat rule.** If stuck on the same thing for 3 consecutive heartbeats, either change approach fundamentally or escalate to the investor via `send_message`.
5. **Respect the heartbeat window.** Don't start work you can't make meaningful progress on within the hour. Break it into smaller pieces.
6. **No busywork.** Don't create tasks just to appear productive. If there's genuinely nothing to do (all goals met, all tasks done), log "idle — no pending work" and use the time for capability discovery or reflection.

## Escalation During Heartbeat

Only escalate to the investor when:
- A task is blocked for 3+ heartbeats and all approaches have been tried
- A financial decision exceeds the spending threshold in `bank/index.md`
- A legal or irreversible action needs investor awareness
- There's genuinely no path forward on a critical item

When escalating, include:
- What's stuck
- What approaches have been tried
- What options remain
- Your recommendation (investor can override, but always bring a recommendation)