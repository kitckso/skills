# Agent Skills

A personal collection of skills developed to optimize AI agent workflows.

## Skills

### [`ask-for-help`](./skills/ask-for-help/SKILL.md)

Use this when running a cheap or fast LLM as your agent and it hits a problem it cannot solve — complex logic, architectural decisions, important features, or better UI design.

**Why this exists:** The best coding LLMs (like Claude) are expensive, but many of them can be accessed for free through web chatbots. This skill lets you subscribe to a cheap coding plan (or even a free one) and only escalate the critical parts to a stronger model via copy-paste. The result is near-top-tier quality at minimal cost.

You can also manually trigger this skill by telling the agent to "ask for help" (or similar phrasing) when implementing important or complex logic, or when you want a better UI/UX.

The agent will:

1. Recognize it is stuck or that the task requires stronger reasoning
2. Collect all relevant context (goal, task, errors, attempts, constraints)
3. Generate a ready-to-copy prompt

You then paste that prompt into any free powerful web chatbot (ChatGPT, Gemini, Claude.ai, etc.), copy the response back to your agent, and the agent continues the task using that guidance. The fast and cheap LLM can then continue working on the remaining simple tasks.

**This keeps your day-to-day work fast and cheap while giving you access to stronger models exactly when it matters.**
