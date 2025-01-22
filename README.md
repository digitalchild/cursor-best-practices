# Cursor Best Practices

Cursor is a powerful AI enabled IDE which is a fork of VS Code. It is extremely powerful and with the right configuration you can speed up your development workflow immensely. The configuration is done though a mixture of `.cursorrules` files, [Rules for AI](https://docs.cursor.com/context/rules-for-ai) and other context files. There are different levels of rules and instructions that you can use to help you build your project.

- Rules for AI: These are general rules you want cursor to follow no matter the technology or project you are working on.
- Cursor Rules: These are specific rules for the project.
- Context Files: These are the full details of the project. This gives cursor the information about what you want to build and how it should be built.

## Rules for AI

Rules for AI are cursor rules that will apply to every project. These are general principles you want cursor to follow no matter the technology or project you are working on.

You can add custom instructions to Cursor by modifying the Rules for AI section under `Cursor Settings > General > Rules for AI`.

Here is an example of a Rules for AI settings you can add to Cursor:

```markdown
## Key Principles:
- Write clean, simple, readable code
- Implement features in the simplest possible way
- Keep files small and focused (<200 lines)
- Test after every meaningful change
- Focus on core functionality before optimization
- Use clear, consistent naming
- Think thoroughly before coding. Write 2-3 reasoning paragraphs.
- ALWAYS write simple, clean and modular code.
- use clear and easy-to-understand language. write in short sentences.
- When making changes to existing files, make sure you're not removing existing code that is required. 

## Error Fixing
- DO NOT JUMP TO CONCLUSIONS! Consider multiple possible causes before deciding.
- Explain the problem in plain English
- Make minimal necessary changes, changing as few lines of code as possible
- In case of strange errors, ask the user to perform a web search to find the latest up-to-date information

## Building Process
- Verify each new feature works by telling the user how to test it
- DO NOT write complicated and confusing code. Opt for the simple & modular approach.
- when not sure what to do, tell the user to perform a web search

## Comments
- ALWAYS try to add more helpful and explanatory comments into our code
- NEVER delete old comments - unless they are obviously wrong / obsolete
- Include LOTS of explanatory comments in your code. ALWAYS write well documented code.
- Document all changes and their reasoning IN THE COMMENTS YOU WRITE
- when writing comments, use clear and easy-to-understand language. write in short sentences.
```

## Cursor Rules Files

When starting any new project, the first thing you should do is create a new `.cursorrules` file for the project. The `.cursorrules` file is the general information that you want cursor to know about the project and what to follow. Such as the php version, telling it to always follow WordPress coding standards, etc.

Each project will have its own `.cursorrules` file. The file will be located at the root of the project directory. The details in this file will be more specific to the project and tehcnical you are working with.

## Examples

- [WordPress Plugin](.cursorrules.wordpress.example) - This is an example of a `.cursorrules` file for a WordPress plugin project. This file will contain rules for the project such as coding standards, file structure, naming conventions, etc.
- [Django Project](.cursorrules.django.example) - This is an example of a `.cursorrules` file for a Django project. This file will contain rules for the project such as coding standards, file structure, naming conventions, etc.

## Context files

Context files are the files where you outline as much information as you can about the project. This is the context that you will provide cursor as you work through the various steps of the project. At the very least you should have an `instructions.md` file that outlines the full details of the project.

### Instructions

An `instrucitons.md` file gives the full details of the project. This gives cursor the information about what you want to build and how it should be built. This is your complete project requirements document. It is best to be formatted as a markdown file that contains as much detail as possible about every aspect of the project. You will refer to this file when using composer to work on new features. You should include the steps to build the project. When creating this document, you should think about how you would build the project. What are the steps to build it? What are the files that will be created? What is the structure of the files? What are the dependencies? What are the technologies that will be used?

While the cursor rules file is how you want cursor to work in terms of the kind of developer it should be, the instructions files outlines what the developer will be building.

You might split the instructions files into multiple files if needed. For instances you might have a main project `instructions.md` file, then you might have a `database.md` file that will outline the database schema and and relationships. You might also have a `frontend.md` instructions file that will outline the frontend design and functionality, the UI framework, etc.

### Roadmap

The `roadmap.md` file outlines the planned development trajectory, key milestones, and future features of the project. It serves as a strategic document that prioritizes development phases, tracks major objectives, and provides a clear timeline for implementation, helping team members understand both short-term goals and long-term vision for the project's evolution.

## Cursor Composer

Composer is an AI coding assistant that integrates directly into cursor, designed to help you explore, write, and modify code without disrupting your workflow.

### Key Features

- **Agent Mode (⌘.)**: A proactive coding partner that can:
  - Pull relevant context automatically
  - Execute terminal commands
  - Create/modify files
  - Perform semantic code search
  
- **Normal Mode**: Provides core functionality for:
  - Codebase and documentation search
  - Web search integration
  - File creation and modification
  - Context-aware assistance

### Context Management

- Use @ to access context options
- \# symbol for current open file selection
- Context pills show active reference scope
- @Recommended automatically pulls relevant context in Agent mode

### Code Generation & Safety

- Review changes in diff view
- Accept/reject suggested modifications
- Checkpoint system for version control
- History tracking for previous sessions

### Layouts

- Pane: Split view with chat sidebar
- Editor: Flexible single window view

## Tips

- Do not let the LLM make big decisions. You should always be the one making the decisions.
- Sometimes its better to read the documentation of the services you're using then letting AI try and fail.
- Knowledge cut off can result in the LLM going around in circles and wasting time. Give it 3 attempts to get the answer.
- Whenever you're working on a new feature or request, start a new composer instance.
- When tagging files, always ensure you only include the files needed for the current request.
- You can have cursor index your own documentation or documentation from other sources.
- Include the full path of the file at the top of every file you create.

## How to get started

When you are ready, open composer and add the instructions file to the context. The first think you should do is to ask composer the following question:

```plaintext
Can you please review the instructions and see if you have any questions before you start. Think about the project and the steps to build it. 
```

If it has no questions, then you can tell it to start at step 1. After step 1 is complete, now you should review the code and ensure that it is correct. If it is not, you can ask it to fix the code.


## Resources

- <https://cursor.directory/> - A directory of cursor rules files for various projects.
- <https://www.youtube.com/watch?v=gYLNxUxVomY> - A video from David Ondrej on how to use Cursor.
