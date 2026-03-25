# Claude Code: Best Practices & Efficiency Guide

This guide summarizes key strategies for using **Claude Code** effectively, focusing on workflow optimization, token management, and advanced automation using hooks.

---

## Workflow & Architecture

* **The Initial Scan (`/init`)**: Always start a new project with `/init`. This allows Claude to index the codebase and understand the folder structure.
    * *Efficiency Tip*: Run this only once. For ongoing context, maintain a central `.md` file for project rules instead of re-running `/init` multiple times.
* **The "Plan-First" Strategy**: 
    1.  **Phase 1 (Plan)**: Use **Claude 3.5 Opus** to define the logic, structure, and edge cases.
    2.  **Phase 2 (Act)**: Switch to **Sonnet** or **Haiku** for the actual implementation to save on costs and latency.
* **Context Tagging**: Use the `#` symbol in your Markdown files or prompts to explicitly link specific files as context.
* **Compact Mode**: Use the `/compact` command when exploring a codebase. It provides concise summaries and avoids long-winded explanations that consume unnecessary tokens.

---

## Token Efficiency (Save Your Burn Rate)

To keep your costs down and stay within rate limits, follow these "Lean Coding" principles:

* **Minimalist Setup**: Use small, focused prompts. Avoid "mega-prompts" that force Claude to process too much information at once.
* **Stop Re-reading Files**: If Claude has already indexed a file and it hasn't changed, don't ask it to read it again.
* **Use `.claudeignore`**: Similar to `.gitignore`, use this to prevent Claude from scanning `node_modules`, logs, or large build artifacts. This drastically shrinks the context window.
* **Focused Scope**: Instead of letting Claude roam the whole repo, tell it: *"Only focus on the `/api/routes` directory for this task."*

---

## Claude Hooks (Automation)

Hooks are one of Claude Code's most underrated features. They allow you to automate repetitive tasks during your dev session.

| Hook Type | Description | Practical Use Case |
| :--- | :--- | :--- |
| **`on_init`** | Runs when you start Claude Code. | Checking for dependency updates or setting ENV variables. |
| **`pre_command`** | Executes before a command runs. | Running a linter (`eslint`) to catch syntax errors early. |
| **`post_command`** | Executes after a command finishes. | Auto-running tests (`npm test`) after Claude modifies a file. |

---

### How to use this file:
1.  Create a file named `CLAUDE_GUIDE.md` in your GitHub repository.
2.  Paste the content above.
3.  Commit and push: `git add CLAUDE_GUIDE.md && git commit -m "docs: add comprehensive Claude Code guide"`

---

## Reference & Further Reading
* [**12 Proven Techniques to Save Tokens in Claude Code**](https://aslamdoctor.com/12-proven-techniques-to-save-tokens-in-claude-code/) – A comprehensive guide on reducing your API burn rate.
* [**Claude Code's Underrated Feature: Hooks**](https://www.reddit.com/r/ClaudeAI/comments/1qlzxr1/claude_codes_most_underrated_feature_hooks_wrote/) – Community discussion and real-world examples of using hooks to automate your workflow.
* [**Claude Code Official Documentation**](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code) – The ultimate source for CLI commands and updates.
