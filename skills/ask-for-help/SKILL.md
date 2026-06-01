---
name: ask-for-help
description: Use when the agent cannot solve a problem, encounters errors it cannot fix, lacks domain knowledge, hits repeated failures, or when the user explicitly requests help from a stronger model or agent
---

# Ask for Help

## Overview

When you cannot reliably solve a problem, generate a structured handoff prompt for the user to copy into a stronger LLM or agent. The user pastes the response back, and you continue using that guidance.

**Core principle:** Never guess or fabricate a solution. Escalate honestly and give the stronger model maximum context to help.

## When to Use

- Task exceeds your reasoning capability
- Multiple failed attempts at the same problem
- Domain knowledge you lack (specialized APIs, complex algorithms, architectural decisions)
- Errors or stack traces you cannot diagnose
- User explicitly asks you to get help from a stronger model
- You are uncertain and the cost of being wrong is high

**When NOT to use:**
- You can solve it confidently — just solve it
- The problem is a simple lookup or standard practice
- User has already provided the answer and you just need to apply it

## Core Pattern

### Step 1: Recognize the Escalation Trigger

Stop attempting the task. Do not guess. Acknowledge the limitation clearly:

> I'm not confident I can solve this correctly. Let me generate a prompt you can send to a stronger AI for help.

### Step 2: Gather Context

Before generating the prompt, collect and organize:

| Field | Required | Description |
|-------|----------|-------------|
| **User Goal** | Yes | What the user is ultimately trying to accomplish |
| **Current Task** | Yes | The specific step or subtask that is blocked |
| **Blocking Issue** | Yes | The exact problem, error, or gap preventing progress |
| **Context** | No | Relevant code, file paths, environment, tech stack |
| **Constraints** | No | Requirements, limitations, preferences the user specified |
| **Known Information** | No | What you have already established or confirmed |
| **Attempts** | No | What you tried and why it failed (include errors verbatim) |

### Step 3: Generate the Handoff Prompt

Present the user with a clearly delimited prompt block they can copy:

```
I need assistance from a stronger AI model to continue.

Please copy everything between the START and END markers below
and paste it into a stronger LLM (e.g., Claude Opus, GPT-4, etc.).
Then paste the complete response back here so I can continue.

========== START PROMPT ==========

You are a highly capable AI assistant. Another AI agent needs your
help solving a problem it cannot handle on its own. Please provide
a thorough, actionable response.

## User Goal
[What the user is trying to accomplish]

## Current Task
[The specific blocked step]

## Blocking Issue
[Exact problem, error message, or knowledge gap]

## Relevant Context
[Code snippets, file paths, environment details, tech stack]

## Constraints
[Requirements or limitations]

## What Has Been Tried
[Previous attempts and their results, including error messages verbatim]

## What Is Already Known
[Confirmed facts, working components, ruled-out causes]

## Requested Help
Please provide:
1. Analysis of the root cause or core issue
2. A recommended solution with step-by-step instructions
3. Any code, commands, or configuration needed
4. Assumptions you are making
5. Anything the requesting agent should watch out for

Keep your response concrete and actionable — another AI agent
will use it to continue the work.

========== END PROMPT ==========
```

### Step 4: Receive and Apply the Response

When the user pastes the stronger model's response:

1. Read the full response carefully
2. Extract the recommended solution and steps
3. Apply the guidance to the original task
4. If the response is unclear or incomplete, ask the user specific clarifying questions
5. If the response reveals the problem is deeper than expected, say so — do not pretend it is resolved

## Quick Reference

```
Trigger     →  Recognize you are stuck or asked to escalate
Collect     →  Goal, task, blocker, context, attempts
Generate    →  Structured prompt with clear delimiters
Handoff     →  User copies to stronger LLM
Receive     →  User pastes response back
Continue    →  Apply guidance, resume work
```

## Common Mistakes

| Mistake | Fix |
|---------|-----|
| Generating a vague prompt without error details | Always include verbatim errors and specific file/code context |
| Guessing instead of escalating | If you have failed twice at the same issue, escalate |
| Ignoring parts of the stronger model's response | Read and apply the full response before continuing |
| Not telling the user what you are doing | Clearly explain why you are escalating and what to do |
| Fabricating context to fill optional fields | Leave optional fields out rather than guessing |
| Continuing to retry after deciding to escalate | Stop retrying — generate the prompt immediately |

## Red Flags — Escalate Now

- You are about to try the same approach a third time
- You are writing code you do not understand
- You are guessing at API behavior without documentation
- The error message means nothing to you
- You catch yourself saying "maybe if I try..."
- The user looks frustrated with repeated failures
