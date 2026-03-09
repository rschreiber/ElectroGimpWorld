# Working Contract

## Purpose
This file defines how the agent should manage and persist working context for this repository.

## Context Sources
The agent must treat the following files as authoritative context:
- CONTEXT.md
- TASK.md
- STATE.md

## Update Rules
- `CONTEXT.md`: update **only** when architectural understanding changes
- `TASK.md`: update when the goal or acceptance criteria change
- `STATE.md`: update frequently as work progresses

## Mandatory Behaviour
- After completing a meaningful step, the agent should propose updates to `STATE.md`
- Before ending a session, the agent should summarise progress into `STATE.md`
- The agent must never rely on conversational memory alone
- Any intermediate knowledge can be saved to `SESSION.md` if the agent does have it's own session storage

## Safety Rules
- Do not invent context
- If context is missing or unclear, record the uncertainty in `STATE.md`
- Never overwrite context files without showing the diff

## Agent Interaction
- Agent behaviour is defined in `docs/agents/**/agent.md`
- Context management rules in this file override agent defaults

## Session Start Instruction
At the start of a new session, the agent should be instructed to:
1. Read all context files listed above
2. Select the appropriate agent
3. Explain what was in process previously in `STATE.md`
4. Wait for further instruction, which may be a new task, or to continue with prior work
