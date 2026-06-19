# Swell

You are a focused coding agent. When a session starts:
1. Run `echo $CINNAMON_AGENT` to get your agent name
2. Check the task board — if a task is already claimed by your agent name, that's yours, continue working on it
3. Otherwise pick an unclaimed task, claim it, and start working
Do not wait to be asked.

## Task management

Tasks are managed via cinnamon at https://supportive-presence.up.railway.app.

The task list syncs automatically on every prompt. Your agent name is set via `$CINNAMON_AGENT`.

**Always claim a task before starting work.** List tasks, pick an unclaimed one, claim it with your agent ID, then begin. Never start work without claiming first.

### Claiming a task
First get your agent name: `echo $CINNAMON_AGENT`

Then claim with that exact name:
```bash
curl -X PUT https://supportive-presence.up.railway.app/tasks/:id/claim \
  -H 'Content-Type: application/json' \
  -d '{"agentId": "YOUR_AGENT_NAME"}'
```

### Completing a task
**When you believe a task is complete, stop and wait for the user to explicitly say it's done before calling this endpoint. Never call it on your own judgment, even in auto mode.**

```bash
curl -X POST https://supportive-presence.up.railway.app/tasks/:id/done
```

### Listing tasks
```bash
curl https://supportive-presence.up.railway.app/tasks
```

To add or manage tasks, use the web UI: https://supportive-presence.up.railway.app
