# Universal Best Practices Template for Code Agents

This file defines the **recommended universal structure** for **Code Agent** guideline files. Generated content should always focus on the *project's* business and architectural rules, adopting the latest prompt engineering practices for autonomous agents.

## Golden Rules for Content Generation:
- **Imperative Language**: Use direct orders (e.g., "Use `withRetry()` for API calls") instead of descriptions (e.g., "The project uses retry"). This drastically increases the **Code Agent's** compliance rate.
- **Focus on "The Unspoken"**: Don't waste space listing rules that a linter already catches. Focus on design decisions and architectural "gotchas."
- **Canonical Examples**: Point to a real reference file (e.g., "For the controller pattern, see `src/controllers/UserController.ts`").
- **Be Concise**: Avoid Context Bloat to prevent degrading the agent's performance.

## File Strategy (Root vs. Modular)

If the project is complex or a monorepo, use a modular strategy to ensure the **Code Agent** loads only the relevant context for the folder it is working in:

1. **Root File (`/CLAUDE.md`, `/AGENTS.md`, etc.)**:
   - Acts as a **Global Repository Map**.
   - **Must contain**: Overview, global commands (e.g., docker), and instructions for the Agent to read modular files in subfolders.

2. **Modular Files (`/frontend/CLAUDE.md`, etc.)**:
   - Act as **Specialized Dynamic Context**.
   - **Must contain**: Only the technological and style rules for that specific folder (e.g., React rules vs. Database rules).

---

Regardless of the destination file (`CLAUDE.md`, `GEMINI.md`, `AGENTS.md`, or `.github/copilot-instructions.md`), each file's content should cover the sections below (adapted to the folder's scope):

## 1. Scope Overview (Context)
- **Purpose**: What the project (or this folder) does in 1-2 sentences.
- **Domain**: Core business rules and jargon.

## 2. Essential Commands (Tooling)
*Provide validated exact terminal commands.*
- **Build / Dev**: How to run locally.
- **Test**: The exact test command (e.g., `npm run test:unit`).
- **Lint**: Style validation command.

## 3. Architecture Patterns and Directories
- **Where the code lives**: Explain the function of key directories.
- **Tests**: Say where to create them and what the suffix pattern is.
- **Canonical Example**: "To understand our standard architecture, see the file `[REAL FILE]`."

## 4. Code Patterns and Restrictions ("Gotchas")
- **Imperative Rules**: Write in a direct order format.
- **What to Avoid**: Strong restrictions that protect system integrity.

---

**Note for the Skill**: Extract REAL data from the repository to fill this structure. Turn your findings into imperative and concise rules.
