# Test Writer Prompt — Write Cypress Tests

Paste this prompt into a Claude session inside your project to start writing Cypress tests using the test writer agent.

**Prerequisite:** Cypress must already be installed in your project (via the setup agent or manually).

---

## Prompt

```
I want to write Cypress tests for this project using the Cypress Agentic Kit.

Please do the following:

1. Read `knowledge-base/00-master.md` to understand the knowledge base structure.

2. Assume the role of `cypress-test-writer-agent` by reading `agents/cypress-test-writer-agent.md`.

3. Execute the test writing runbook from `knowledge-base/02-test-writing.md`:
   - Run pre-flight checks (verify Cypress is installed, read config, check existing tests and custom commands)
   - Detect or create the project structure file
   - Then ask me what feature or flow I want to test, and the Figma frame URL for the design

4. When writing tests:
   - Show me the complete test code before creating any files
   - Add data-cy attributes to the application source code where needed
   - Place tests in the correct category folder (smoke/regression/integration/functional)
   - Follow existing conventions if tests already exist in the project

Important:
- Do not guess what to test — ask me.
- Do not modify application code beyond adding data-cy attributes.
- Show me every file change before making it.
- Give me a summary after writing each test.
- If a Figma URL is provided, use it to validate that the Cypress tests cover all components, states, and interactions visible in the design. Use Figma component names to inform data-cy attribute naming. Extract visual properties (font sizes, colors, padding, margins) from Figma to generate CSS assertion tests where applicable.
```

---

## What Happens When You Run This

1. The agent runs pre-flight checks to verify Cypress is ready.
2. It reads or creates a project structure file to understand your codebase.
3. It asks you what feature or flow you want to test, and the Figma frame URL for the design.
4. For each test, it:
   - Shows the test code and data-cy attributes before creating files
   - Waits for your confirmation
   - Creates the test file and adds selectors to your app code
   - Gives you a summary with the command to run the test

## After Writing Tests

- Run a specific test: `npx cypress run --spec "cypress/e2e/<category>/<test>.cy.ts"`
- Run all tests: `npx cypress run`
- Run in interactive mode: `npx cypress open`
