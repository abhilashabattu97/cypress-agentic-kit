# Cypress Agentic Kit

An AI-driven kit that automates Cypress setup in any project — Node or non-Node — using a knowledge base and agent architecture.

## What This Does

A single prompt installs a Cypress knowledge base and setup agent into your project. The agent reads the knowledge base and automatically:

- Checks if Node.js is installed (installs it with your consent if not)
- Detects your package manager (npm / yarn / pnpm)
- Handles non-Node projects (Laravel, Django, Rails, etc.) by creating a minimal Node setup
- Installs Cypress as a dev dependency
- Scaffolds config, support files, and directory structure
- Validates the setup and gives you a final report

No scripts to run. No dependencies to install. Just one prompt.

## How to Use

### 1. Open your project in Claude

Open a Claude session (Claude Code, Cursor, or any Claude-integrated IDE) inside the project where you want Cypress.

### 2. Paste the bootstrap prompt

Copy the prompt from [`prompts/bootstrap.md`](prompts/bootstrap.md) and paste it into your Claude session.

### 3. Follow the agent

The agent will walk through the setup step by step, asking for your input only when needed (e.g., Node installation consent, project-specific config).

### 4. Done

You'll get a final report showing what was installed and the status of each step. Start writing tests in `cypress/e2e/`.

## Project Structure

```
cypress-agentic-kit/
├── CLAUDE.md                          # Rules for how agents read the KB
├── README.md                          # This file
├── knowledge-base/
│   ├── 00-master.md                   # Index — lists all sections + agent mappings
│   └── 01-setup-run.md               # Setup runbook (11 steps)
├── agents/
│   └── cypress-setup-agent.md         # Setup agent prompt
└── prompts/
    └── bootstrap.md                   # One prompt to install everything
```

## Works With Any Project

| Project Type | What Happens |
|-------------|--------------|
| Node project (React, Next.js, Angular, Vue) | Detects package manager, installs Cypress |
| Non-Node project (Laravel, Django, Rails, WordPress) | Creates minimal package.json, installs Cypress |
| No Node.js on machine | Installs Node.js with your consent, then proceeds |

## What's Coming Next

| Phase | What |
|-------|------|
| Phase 2 | Test writing standards KB + test writer agent |
| Phase 3 | Manual test case generator agent |
| Phase 4 | Project config KB (base URL, auth, environments) |
| Phase 5 | CI integration KB + CI agent |

## Design Principles

- **One prompt installs everything** — no manual file creation
- **Agents read only what they need** — minimal token usage, no hallucination from context overload
- **Idempotent** — safe to run multiple times, skips what's already done
- **Works without the KB** — if knowledge base is missing, agents degrade gracefully
- **User prompt always wins** — KB is supplementary context, never an override
