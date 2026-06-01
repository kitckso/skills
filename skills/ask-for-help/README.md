# Ask for Help

A skill that delegates complex problems to a stronger AI model. When the agent hits a problem it cannot solve — complex logic, architectural decisions, or errors it cannot diagnose — it generates a structured handoff prompt for you to copy into a more capable LLM (ChatGPT, Claude.ai, Gemini, etc.). You paste the response back, and the agent continues the work.

## How to Trigger

### Automatic

The agent will automatically trigger this skill when it detects it is stuck — for example, after multiple failed attempts at the same problem, encountering errors it cannot diagnose, or when a task exceeds its reasoning capability.

### Manual

You can manually trigger this skill at any time by telling the agent to **"ask for help"** (or similar phrasing like "escalate this" or "get help from a stronger model"). Use this when you want a stronger model to handle complex logic, architecture decisions, or UI design.

## When to Use

- The agent is stuck on the same problem after multiple attempts
- Complex logic, architecture decisions, or UI design is needed
- Errors or stack traces the agent cannot diagnose
- You explicitly want a stronger model to take over a specific task
- The cost of being wrong is high

## How It Works

1. The agent recognizes it is stuck or you ask it to escalate
2. It collects all relevant context — goal, task, errors, attempts, constraints
3. It generates a delimited prompt you can copy in one click
4. You paste that into a stronger model (ChatGPT, Claude.ai, Gemini, etc.), then paste the response back
5. The agent continues using that guidance

This keeps your day-to-day work fast and cheap while giving you access to stronger reasoning exactly when it matters.

See [`SKILL.md`](./SKILL.md) for the full implementation and all instructions.
