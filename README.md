# Cursor Best Practices

[Cursor](https://www.cursor.com/) is a powerful AI enabled IDE which is a fork of VS Code. It is extremely powerful and with the right configuration and understanding of how to use it, you can speed up your development workflow immensely. The configuration is done though a mixture of [Rules for AI](https://docs.cursor.com/context/rules-for-ai),  `.cursorrules` files, and other context files. There are different levels of rules and instructions that you can use to help you build your project.

- Rules for AI: These are general rules you want cursor to follow no matter the technology or project you are working on.
- Cursor Rules: These are specific rules for the project.
- Context Files: These are the full details of the project. This gives cursor the information about what you want to build and how it should be built.

Once you have configured cursor, the next steps are to learn the other functionalities of the IDE. This will result in better code generation and increase your productivity immensely.

## Configuration

### Rules for AI

Rules for AI are the global cursor rules that will apply to every project. These are general principles you want cursor to follow no matter the technology or project you are working on.

You can add custom instructions to Cursor by modifying the Rules for AI section under `Cursor Settings > General > Rules for AI`.

Here is an example of a Rules for AI settings you can add to Cursor:

```markdown
## Key Principles:
- Write clean, simple, readable code
- Treat me as an expert, skipping unnecessary explainations 
- Avoid high-level overviews; focus on the details
- If you don't know the answer, ask for clarification
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

### Cursor Rules Files

When starting any new project, the first thing you should do is create a new `.cursorrules` file for the project. The `.cursorrules` file is the technical information that you want cursor to know about the project and what to follow. Such as the php version, telling it to always follow WordPress coding standards, etc.

Each project will have its own `.cursorrules` file. The file will be located at the root of the project directory. The details in this file will be more specific to the project and the tehcnical stack you are working with.

#### Understanding the Benefits of .cursorrules

The .cursorrules configuration is an essential component in Cursor AI development that enables developers to set custom parameters for AI interactions. Here are the key advantages:

1. AI Response Customization: Configure the AI to better understand and respond to your specific project requirements, resulting in more precise code output.

2. Standardization: Implement uniform coding patterns by establishing development guidelines in your .cursorrules configuration, maintaining consistency across your codebase.

3. Enhanced Project Understanding: Feed the AI vital project information like common functions, design patterns, and library preferences to receive more contextually appropriate suggestions.

4. Development Efficiency: Minimize post-generation edits through well-structured rules, streamlining your coding workflow.

5. Collaborative Harmony: Share a unified .cursorrules configuration among team members to ensure everyone receives consistent AI support and maintains coding uniformity.

6. Project-Centric Solutions: Incorporate details about your project's architecture, dependencies, and specific requirements to receive more targeted and relevant AI assistance.

#### What should you include in your `.cursorrules` file?

- System prompt
- Project Description
- Key Principles
- Project Structure
- Tech Stack/Project Dependencies
- Naming Conventions
- Coding Standards
- UI/UX Guidelines
- Language specific guidelines
- Environment specific guidelines
- State Management
- Testing
- Security
- Git Usage
- Documentation and Comments
- Development Workflow
- Build Process
- CI/CD
- Anything else that you think is important to know about the project is built from a techincal point of view.

#### Example Cursor Rules Files

- [WordPress Plugin](.cursorrules.wordpress.example) - This is an example of a `.cursorrules` file for a WordPress plugin project.
- [Django Project](.cursorrules.django.md) - This is an example of a `.cursorrules` file for a Django project.
- [Playwright Project](.cursorrules.playwright.wordpress.js.md) - This is an example of a `.cursorrules` file for a Playwright project in Javascript for WordPress.

### Cursor ignore files

You can include files in a `.cursorignore` file to tell cursor to ignore certain files from indexing. This is useful for ignoring files that are not needed for the project. If you already have a `.gitignore` file, cursor will automatically use that file to ignore files from indexing. However if you have other files you want to ignore, you can add them to the `.cursorignore` file.

A good example of files to ignore would be if you were refactoring a project and you have legacy code that you don't want to touch. You can add the legacy code to the `.cursorignore` file to tell cursor to ignore it.

```plaintext
# Cursor ignore file

legacy-code/
```

Please Note: This file is only for project indexing. Chat and composer will still have access to all files.

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

## Context files

Context files are the files where you outline as much information as you can about the project. This is the context that you will provide cursor as you work through the various steps of the project. At the very least you should have an `instructions.md` file.

### Instructions file

An `instructions.md` file gives the full details of the project. This gives cursor the information about what you want to build and how it should be built. This is your complete project requirements document. It is best to be formatted as a markdown file that contains as much detail as possible about every aspect of the project. You will refer to this file when using composer to work on new features. You should include the steps to build the project. When creating this document, you should think about how you would build the project. What are the steps to build it? What are the files that will be created? What is the structure of the files? What are the dependencies? What are the technologies that will be used?

While the cursor rules file is how you want cursor to work in terms of the kind of developer it should be, the instructions files outlines what the developer will be building.

You might split the instructions files into multiple files if needed. For instance, you might have a main project `instructions.md` file, then you might have a `database.md` file that will outline the database schema and relationships. You might also have a `frontend.md` instructions file that will outline the frontend design and functionality, the UI framework, etc.

It's best to work through the instructions file in a state of the art model to create the best possible instructions file. Something like Claude 3.5 or OpenAI's o1 model. Have a discussion with the LLM to work through your project. Ask it to provide a clear, detailed overiew of a the project as a Project Requirements Document in markdown format.

#### Example Prompt for the Instructions File

```plaintext
You are a senior Business Analyst with 10+ years of experience in creating project requirements documentation. Your expertise includes gathering stakeholder requirements, technical analysis, and creating clear, actionable documentation that bridges business needs and technical implementation.

Your responses should:

- Follow industry best practices for requirements documentation
- Use clear, unambiguous language
- Include appropriate level of detail for both business and technical audiences
- Focus on both functional and non-functional requirements
- Highlight dependencies and constraints
- Suggest validation methods and acceptance criteria
- Include traceability to business objectives
- When asked about requirements documentation, provide structured, professional responses that demonstrate:

Deep understanding of requirements gathering methodologies
- Clear organization and formatting
- Risk awareness and mitigation strategies
- Stakeholder consideration
- Technical feasibility awareness
- Always maintain a balanced perspective between business needs and technical constraints while ensuring requirements are SMART (Specific, Measurable, Achievable, Relevant, Time-bound).

I want you to create a detailed Project Requirements Document based on the information below. Start by asking me a few questions to clarify the project to make sure you understand the project requirements. If I am missing any information, please ask me to provide it or clarify it. We will start with the project overiview and then work through each section of the project to ensure we have a detailed and comprehensive project requirements document.

I am building a [Project Name] project.

Here is a brief overview of the project:

[Overview of the project]

Here are the key features of the project: 

[Key features of the project]

Here are the core functionalities of the project:

[Core functionalities of the project]

Here are the core technologies that will be used:

[Core technologies that will be used]
```

### Roadmap file

The `roadmap.md` file outlines the planned development trajectory, key milestones, and future features of the project. It serves as a strategic document that prioritizes development phases, tracks major objectives, and provides a clear timeline for implementation, helping team members understand both short-term goals and long-term vision for the project's evolution.

This file should contain any future features that you plan to add to the project. It should also contain the key milestones that you plan to achieve. This will help you stay on track and ensure that you are building the project in the correct order. This can also be used by composer to help you build the project.

## Cursor Commands

Cursor has a number of commands you can use that can provide more context to the AI when interacting with it. All commands are started with an `@` symbol.

### Files

`@Files` gives you the ability to include specific files to the current chat, cmd K or composer. Cursor will show you the path of the files so that you can ensure you are including the correct files. This is particularly useful when you are looking to duplicate structure from one part of the codebase to another.

### Folders

Like the files command, the `@Folders` command allows you to include specific folders to the current chat or composer. This is useful when you are working on a new feature and need to include the relevant files for the feature.

### Code

The `@Code` command allows you to reference a specific section of code within a file. You can also add the selected code by using cmd L and it will be added to the current composer or chat.

### Docs

`@Docs` is an extremely powerful and underrated feature. This allows you to give the AI up to date documentation to reference when writing code. This will help reduce hallucinations and stop it from using depracted calls/methods. Cursor includes a number of popular indexed documentation sets. You can see the full set available [here](https://raw.githubusercontent.com/getcursor/crawler/main/docs.jsonl).

You can also give your own documentation to the system by adding them to cursor. This is done by using `@Docs` and `Add New Doc`. You provide it with the URL, prefix and a name. Cursor will then index the documentation and you will be able to reference it like other docs.

Please note: Include the trailing slash `/` in the URL. To include all sub pages in the indexing.

### Web

`@Web` allows you to search the web for information. This is useful when you are looking for the most up to date information about a new feature or technology. This helps with reducing the need for you to manually search the web.

## Other commands

There are several other commmands available which are you can learn about in the official [Cursor Documentation](https://docs.cursor.com/context/@-symbols/).

## Screenshots

Both chat and composer support file attachments. This is very useful when you are working with your UI and you have a specific screenshot you want to generate. Say you have a figma file and you need a UI component to be generated, you can attach the figma file and use the screenshot command to generate a screenshot of the UI component. 

## Tips

- Do not let the LLM make big decisions. You should always be the one making the decisions.
- Sometimes its better to read the documentation of the services you're using then letting AI try and fail.
- Knowledge cut off can result in the LLM going around in circles and wasting time. Give it 3 attempts to get the answer.
- Whenever you're working on a new feature or request, start a new composer instance.
- When tagging files, always ensure you only include the files needed for the current request.
- You can have cursor index your own documentation or documentation from other sources.
- Include the full path of the file at the top of every file you create. 
- Always ask the LLM to review the instructions and see if it has any questions before you start. Think about the project and the steps to build it. 
- Always have your cursor rules file ready before you start.
- Spending more time with your cursor rules file and instructions file will result in better code generation.

## Resources

- <https://cursor.directory/> - A directory of cursor rules files for various projects.
- <https://www.youtube.com/watch?v=gYLNxUxVomY> - A video from David Ondrej on how to use Cursor.
- <https://dotcursorrules.com/> - A website that has a collection of cursor rules files for various projects.
- <https://github.com/PatrickJS/awesome-cursorrules> - Awesome Cursor Rules
