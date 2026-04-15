---
name: init-code-agent
description: Configures Git repositories by identifying best practices and generating the correct context files for Code Agents (CLAUDE.md, GEMINI.md, AGENTS.md, .github/copilot-instructions.md).
---

# Code Agent Configurator (init-code-agent)

This skill automates the creation of guideline files for **Code Agents**. A project's best practices (architecture, testing, code standards) are universal. Only the format/destination file changes depending on the user's preferred tool.

## Required Workflow

1. **Tool Identification**:
   - **ALWAYS** start by using the `ask_user` tool to ask the user which Code Agent they want to configure.
   - **Options to display in `ask_user`:**
     - Claude Desktop / Code (`CLAUDE.md`)
     - Gemini CLI (`GEMINI.md`)
     - GitHub Copilot (`.github/copilot-instructions.md`)
     - Cursor / Windsurf / Others (`AGENTS.md`)
     - All of the above

2. **Universal Codebase Investigation**:
   - After the selection, use your available file reading and directory searching tools to map the project's universal rules.
   - **Subdomain Identification (Monorepos/Layers):** Check if the project has distinct and segregated technological domains (e.g., `frontend/`, `backend/`, `api/`, `web/`, `packages/` folders).
   - Identify the Tech Stack (`package.json`, `Cargo.toml`, `requirements.txt`, etc.) at both the root and subdomains.
   - Analyze the Basic Architecture (where tests are, where the source code is, naming conventions).

3. **Unified and Modular Content Generation**:
   - For simple projects: create a single set of rules.
   - **For complex projects/monorepos:** plan to create a global context file (at the root) with general rules, and **granular modular files** within each main subdomain (e.g., React-specific rules only inside `frontend/CLAUDE.md` or `frontend/AGENTS.md`). This allows the Code Agent to load rules dynamically only when entering the folder.
   - Refer to `references/templates.md` for the recommended universal content structure for Agents.

4. **File(s) Writing**:
   - Write the generated content to the file (or files, if modular) corresponding to the tool selected in Step 1.
   - If the user chose "All of the above", write the SAME unified content to separate files: `CLAUDE.md`, `GEMINI.md`, `AGENTS.md`, and `.github/copilot-instructions.md`.
   - Format the content in clear, readable Markdown, optimized for LLM consumption.

## Usage Example
1. User: "Configure this repo for Code Agents."
2. You (using `ask_user`): Present the tool options.
3. User selects: "Cursor / Windsurf / Others (`AGENTS.md`)"
4. You: Analyze the code, compile universal best practices, and save everything to the `AGENTS.md` file.
