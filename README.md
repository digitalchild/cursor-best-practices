# Cursor Best Practices

[Cursor](https://www.cursor.com/) is a powerful AI-enabled IDE, forked from VS Code. With proper configuration and usage, it can significantly boost your development speed and code quality. Configuration is done through a combination of **Rules**, `.cursor/rules/*.mdc` files, and context documents like `instructions.md`.

There are multiple layers of rules you can use to instruct Cursor how to behave:

* **User Rules**: Global to your Cursor environment. Defined in settings and always applied.
* **Project Rules**: Stored in `.cursor/rules/` as `.mdc` files and version-controlled per project.
* **Legacy `.cursorrules`**: Still supported but deprecated.

---

## Rule Precedence

Cursor evaluates rules in the following order of priority:

1. **Local (manual)**: Explicitly included with `@ruleName`
2. **Auto Attached**: Files matching glob patterns are referenced
3. **Agent Requested**: AI chooses to include if needed
4. **Always**: Automatically included in all contexts

---

## User Rules (Global Settings)

User Rules are defined via **Cursor Settings > Rules**. These are plain text instructions applied to all projects.

Example:

```text
Please reply in a concise style. Avoid unnecessary repetition or filler language.
```

Use User Rules to set:

* Response language or tone
* Personal coding preferences
* General principles you want the AI to follow globally

> ❗ User rules **do not support** metadata or `.mdc` formatting. They are plain text only.

---

## Project Rules: `.mdc` Files

Project-specific rules live in the `.cursor/rules/` directory. Each rule is saved as a `.mdc` file and can be scoped with globs, included automatically, or triggered manually.

### ✅ Example `.mdc` Rule File:

```md
---
description: RPC Service boilerplate
globs:
  - src/services/**/*.ts
alwaysApply: false
---

- Use our internal RPC pattern when defining services
- Always use snake_case for service names
```

### 🔍 Rule Types:

| Rule Type           | Description                                                                       |
| ------------------- | --------------------------------------------------------------------------------- |
| **Always**          | Always included in context                                                        |
| **Auto Attached**   | Included when referenced files match a glob pattern                               |
| **Agent Requested** | Available to the AI, which decides whether to use it (must include `description`) |
| **Manual**          | Only used when explicitly invoked with `@ruleName`                                |

You can use `@filename.ts` to reference relevant files for the rule.

> To scaffold a new rule in Cursor: use **Cmd + Shift + P > “New Cursor Rule”**.

---

## Understanding the Benefits of `.cursorrules` (now `.mdc`)

Even though the legacy `.cursorrules` file is deprecated, the concept and structure behind it still serve as the foundation for project-based rule design. The updated `.mdc` format continues to support these same benefits:

* **AI Response Customization**: Configure Cursor to respond more accurately to your specific requirements, resulting in better code generation.
* **Standardization**: Establish unified coding guidelines to maintain consistency across your codebase.
* **Enhanced Project Understanding**: Supply the AI with architectural patterns, common libraries, and naming conventions to improve context relevance.
* **Development Efficiency**: Reduce the need for manual corrections by encoding workflows and expectations.
* **Collaborative Harmony**: Shared `.mdc` rules ensure that all team members benefit from the same rule sets and development style.
* **Project-Centric Solutions**: Guide the AI with details about the tech stack, design decisions, and workflow expectations for better assistance.

### What Should You Include in Your `.mdc` Rule Files?

* System prompt
* Project Description
* Key Principles
* Project Structure
* Tech Stack / Project Dependencies
* Naming Conventions
* Coding Standards
* UI/UX Guidelines
* Language-specific guidelines
* Environment-specific guidelines
* State Management
* Testing
* Security
* Git Usage
* Documentation and Comments
* Development Workflow
* Build Process
* CI/CD
* Anything else critical from a technical standpoint

These sections can be distributed across multiple `.mdc` files depending on scope and purpose.

---

## Context Files

These provide project-specific details Cursor uses to guide development.

### `instructions.md`

A full specification of your project:

* Features
* Technologies
* Structure
* Build steps

Split into multiple files if needed (e.g., `frontend.md`, `database.md`).

### Example Prompt to Generate `instructions.md`

```text
You are a senior Business Analyst... [include a structured prompt for LLM assistance]
```

### `roadmap.md`

Outlines milestones and future features to help guide long-term planning and incremental development.

---

## Composer Overview

Composer is Cursor's AI coding assistant for writing and refactoring code interactively.

### Modes

* **Agent Mode (`⌘.`)**: Auto-pulls context, executes commands, edits files.
* **Normal Mode**: File and context-aware assistance.

### Context Commands

* `@Files` – include specific files
* `@Folders` – include folders
* `@Code` – reference specific code blocks
* `@Docs` – reference documentation
* `@Web` – search online

[Full list of @-commands →](https://docs.cursor.com/context/@-symbols/)

---

## Cursor Ignore Files

Use `.cursorignore` to exclude files from indexing. This prevents Cursor from loading unnecessary files into context.

```bash
# .cursorignore
legacy-code/
debug.log
```

> `.gitignore` is respected automatically. This affects indexing only, not chat or composer access.

---

## Tips & Best Practices

* Write focused, composable `.mdc` rules.
* Keep rules concise: under 500 lines.
* Reuse rule blocks instead of duplicating prompts.
* Give rules concrete names and descriptions.
* Use `@filename.ts` references to provide useful anchors.
* Write `instructions.md` before starting AI-based work.
* Always ask Cursor to confirm understanding of tasks first.

---

## Resources

* [https://cursor.directory/](https://cursor.directory/) – Community rule examples
* [https://dotcursorrules.com/](https://dotcursorrules.com/) – More templates
* [https://github.com/PatrickJS/awesome-cursorrules](https://github.com/PatrickJS/awesome-cursorrules) – Community repo
* [Official Cursor Docs – Rules](https://docs.cursor.com/context/rules)
* [Cursor Overview Video](https://www.youtube.com/watch?v=gYLNxUxVomY)
