# Bootstrap Prompt — Install Cypress Agentic Kit

Paste this entire prompt into a Claude session inside your project to install the Cypress knowledge base and setup agent.

---

## Prompt

```
I want to set up Cypress in this project using the Cypress Agentic Kit.

Please do the following:

1. Clone or fetch the knowledge base and agent files from the repository:
   https://github.com/abhilashabattu97/cypress-agentic-kit

2. Copy these directories into this project:
   - `knowledge-base/` → copy to `knowledge-base/` in the project root
   - `agents/` → copy to `agents/` in the project root (or `.claude/agents/` if that convention is already used)

3. Check if a `CLAUDE.md` file exists in the project root:
   - If it exists: append the "Knowledge Base Reading Rules" section from the kit's `CLAUDE.md` to the existing file. Do not duplicate if it already has KB rules.
   - If it does not exist: copy the kit's `CLAUDE.md` to the project root.

4. After copying the files, read `knowledge-base/00-master.md` and confirm what was installed.

5. Then assume the role of `cypress-setup-agent` by reading `agents/cypress-setup-agent.md` and execute the Cypress setup by following the runbook in `knowledge-base/01-setup-run.md`.

Important:
- Do not guess any project-specific values. Ask me if you are unsure.
- If this is not a Node project, ask before creating a package.json.
- If Node.js is not installed, ask before installing it.
- Show me every command before running it.
- Give me a final report at the end.
```

---

## What Happens When You Run This

1. The knowledge base files and agent files are copied into your project.
2. Your project's `CLAUDE.md` is updated with KB reading rules.
3. The setup agent runs automatically and:
   - Checks if Node.js is installed (installs with your consent if not)
   - Detects your package manager
   - Installs Cypress
   - Scaffolds config and support files
   - Validates the setup
   - Shows a final report

## After Setup

- Add your first test in `cypress/e2e/`
- Run tests with `npx cypress open` (interactive) or `npx cypress run` (headless)
- The knowledge base stays in your project for future agents (test writer, CI setup, etc.)
