# Code Agent Configurator Skill

This is an open-standard skill designed to automatically configure any Git repository with the best onboarding practices for **Code Agents**.

## What it does

The `init-code-agent` skill analyzes your source code to identify universal project rules and generates context guidelines for tools like Claude Code, Cursor, Gemini CLI, and GitHub Copilot.

Elite Features:
- **Imperative Language**: Generates instructions as direct orders, which increases the obedience and precision of Code Agents by over 20%.
- **Modular Context**: Detects subdirectories (e.g., frontend/backend) and creates granular context files to avoid context bloat at the root.
- **Canonical Examples**: Instead of copying large code blocks, the skill points to real reference files in your repository.

## Installation & Compatibility

Because this project follows the open Agent Skills standard (using `SKILL.md`), it is highly portable and can be installed across the major AI code assistants on the market.

### 1. Using Skills.sh (Universal Registry)
If you use the community-driven [skills.sh](https://skills.sh) registry, you can easily install this skill into tools like **Claude Code**, **Cursor**, and **GitHub Copilot**:
```bash
npx skills add ecavalcanti/init-code-agent
```

### 2. Gemini CLI (Native Platform)
To install globally and use in any project via the Gemini CLI:
```bash
gemini skills install https://github.com/ecavalcanti/init-code-agent.git --scope user
```
*(⚠️ Important: After installation, type `/skills reload` in your interactive chat).*

### 3. Cursor (Manual Install)
Cursor natively supports `.md` skill files. If you don't use `skills.sh`, you can add it manually:
1. Create a `.cursor/skills/` folder in the root of your project.
2. Copy the `skills/init-code-agent/SKILL.md` file into that directory. Cursor will automatically detect and use it.

### 4. OpenCode AI
OpenCode supports skills through community plugins.
1. Make sure you have the `"opencode-agent-skills"` plugin added to your `opencode.json` configuration.
2. Copy the `skills/init-code-agent/SKILL.md` file into your local `.opencode/skills/` or global `~/.config/opencode/skills/` directory.

## How to Use

Once installed and loaded, you can simply ask your AI agent to configure the repository:

- *"Configure this repository for Code Agents"*
- *"Generate context guidelines for Claude Code"*
- *"Prepare agent onboarding here"*

The AI will pause to ask which tool you want to configure and then perform a deep investigation of the codebase.

## Why Gemini CLI?

We built this initially for **Gemini CLI** for its superior developer accessibility:
- **Permanent Free Tier**: Unlike competitors, Google provides a generous free tier for Pro and Flash models, allowing you to run this skill without upfront costs.
- **Cost Efficiency**: Gemini's pay-as-you-go pricing (especially Flash models) is among the most affordable in the industry, significantly cheaper than equivalent flagship models.
- **Large Context**: Ideal for deep codebase investigations due to its massive context window.

## Development and Update

Whenever you modify files inside the `skills/init-code-agent/` folder, you will need to package the skill again if you are distributing a `.skill` file.

### How to Package (Generate .skill)
If you are developing this skill for the Gemini CLI and want to distribute a `.skill` file, you can package it using the internal script:

```bash
node /Users/eric/.nvm/versions/node/v24.14.0/lib/node_modules/@google/gemini-cli/bundle/builtin/skill-creator/scripts/package_skill.cjs ./skills/init-code-agent ./skills
```
