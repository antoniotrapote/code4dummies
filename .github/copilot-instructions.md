# AI Content Guidelines for code4dummies

## Project Overview
code4dummies is a collection of practical cheat sheets and beginner-friendly guides for developers learning the essentials — from terminal commands to Git, GitHub CLI, and other useful tools to get started in development.
Each guide focuses on explaining the "why" behind every command, not just the "what."

## General Guidelines
- Write for beginners: Assume the reader is new to the topic.
- Be clear and concise: Use simple language and avoid jargon.
- Explain the "why": For each command or concept, explain its purpose and when to use it.
- Use examples: Provide practical examples with realistic output.
- Use Markdown formatting: Utilize headings, code blocks, lists, and tables for clarity.

## When Adding/Updating Content
**DO:**
- Reference real files from the repo (e.g., "see [terminal-cheet-sheet.md](../terminal4dummies/terminal-cheet-sheet.md) for full steps")
- Include practical gotchas (e.g., "detached HEAD" scenario in branch workflow)
- Use tables for command comparisons and option explanations
- Add examples with realistic output

**DON'T:**
- Assume users know Git internals—explain what each command does
- Omit the "why" behind recommendations (e.g., why `--force-with-lease` over `--force`)
- Mix shell-specific syntax without noting the environment
- Create aspirational content—document only what's actively used in this repo

## Licensing
All content should be licensed under CC-BY-NC-4.0 unless otherwise specified.

Include the following license footer in each new .md file:

"CC-BY-NC-4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote)"
