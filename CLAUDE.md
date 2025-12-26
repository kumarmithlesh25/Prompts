# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a curated collection of AI prompt templates organized by domain. It's a documentation-only project with no build system, tests, or dependencies. The prompts are designed to be portable across different AI tools.

## Repository Structure

- `analysis/` - Data summarization, comparative analysis, root cause analysis prompts
- `coding/` - Code review, debugging, explanation, refactoring prompts
- `creative/` - Brainstorming, concept exploration, story framework prompts
- `productivity/` - Task breakdown, decision framework, meeting planning prompts
- `research/` - Topic deep dive, literature review, fact verification prompts
- `writing/` - Content drafting, editing, email composition prompts
- `claude-tutorial/` - Basics of claude-code 


## Prompt Template Format

All prompts follow this structure:

```markdown
## [Prompt Name]
[Brief description]

```markdown
[Prompt with [PLACEHOLDER] variables]
```
```

Placeholders use `[UPPERCASE]` naming to indicate where users should substitute their content.

## Adding New Prompts

1. Place in the appropriate category folder's `prompts.md` file
2. Follow the existing template structure with H2 heading, description, and code block
3. Use descriptive `[PLACEHOLDER]` names for user inputs

## Workflow Preferences

- When adding a file, always ask first
- When committing changes, do not include Claude references in the commit message
