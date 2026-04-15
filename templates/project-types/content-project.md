# Content Writing Project Scaffolding Template

**For AI Assistants**: Follow these instructions to scaffold a content writing project in an empty folder. This project type is for writing articles, books, course material, documentation, or similar long-form content.

---

## Step 1: Ask Follow-Up Questions

Before scaffolding, ask the user:

```
Great — a content writing project! A few quick questions:

1. **What are you writing?**
   - Articles / blog posts
   - A book or e-book
   - Course material / tutorials
   - Technical documentation
   - Mixed / other

2. **Working title or subject?** (e.g., "Guide to Distributed Systems", "My Tech Blog")

3. **Preferred format?** (default: Markdown — alternatives: AsciiDoc, LaTeX, reStructuredText)
```

Use the answers to customize the structure below. Markdown is the default unless the user asks for something else.

---

## Step 2: Create Project Structure

### For Articles / Blog Posts

```
{project_root}/
├── README.md
├── .gitignore
├── outline.md
├── drafts/
│   └── 001-first-article.md
├── published/
├── assets/
│   └── images/
└── templates/
    └── article-template.md
```

### For a Book / E-Book

```
{project_root}/
├── README.md
├── .gitignore
├── outline.md
├── chapters/
│   ├── 00-introduction.md
│   └── 01-chapter-one.md
├── drafts/
├── assets/
│   └── images/
├── appendices/
└── templates/
    └── chapter-template.md
```

### For Course Material / Tutorials

```
{project_root}/
├── README.md
├── .gitignore
├── outline.md
├── modules/
│   └── 01-getting-started/
│       ├── lesson.md
│       ├── exercises.md
│       └── assets/
├── drafts/
├── assets/
│   └── images/
└── templates/
    ├── lesson-template.md
    └── exercises-template.md
```

### For Technical Documentation

```
{project_root}/
├── README.md
├── .gitignore
├── outline.md
├── docs/
│   ├── getting-started.md
│   ├── guides/
│   ├── reference/
│   └── tutorials/
├── drafts/
└── assets/
    └── images/
```

---

## Step 3: Create Root Files

### README.md

```markdown
# {{PROJECT_TITLE}}

{{PROJECT_DESCRIPTION}}

## Structure

| Folder | Purpose |
|--------|---------|
| `drafts/` | Work in progress — rough drafts and ideas |
| `{{CONTENT_FOLDER}}/` | {{CONTENT_FOLDER_DESC}} |
| `assets/` | Images, diagrams, and other media |
| `templates/` | Reusable templates for new content |
| `outline.md` | Overall outline and planning |

## Writing Workflow

1. Plan in `outline.md`
2. Draft in `drafts/`
3. Move to `{{CONTENT_FOLDER}}/` when ready for review
4. {{if articles}} Move to `published/` when final {{/if}}

## Word Count Tracking

| {{UNIT}} | Target | Current | Status |
|----------|--------|---------|--------|
| {{FIRST_ITEM}} | — | 0 | 🚧 In Progress |
```

Where:
- `{{CONTENT_FOLDER}}` = `published` (articles), `chapters` (book), `modules` (course), `docs` (documentation)
- `{{UNIT}}` = "Article" / "Chapter" / "Module" / "Section"

### .gitignore

```gitignore
# OS
.DS_Store
Thumbs.db

# Editors
.vscode/
.idea/
*.swp
*.swo
*~

# Build output (if using static site generator)
_site/
_build/
site/
public/

# PDF builds
*.pdf
!assets/**/*.pdf
```

### outline.md

```markdown
# {{PROJECT_TITLE}} — Outline

## Overview

[High-level description of what this project covers and who it's for]

## Target Audience

[Who is this written for?]

## {{UNIT}} Plan

### 1. {{FIRST_ITEM_TITLE}}
- Key points:
  - [Point A]
  - [Point B]
- Status: 🚧 In Progress

### 2. [Next {{UNIT}}]
- Key points:
  - [Point A]
- Status: ⏳ Planned

## Research & References

- [Link or book title]
- [Link or book title]

## Timeline

| Milestone | Target Date | Status |
|-----------|-------------|--------|
| Outline complete | [Date] | 🚧 |
| First draft | [Date] | ⏳ |
| Review | [Date] | ⏳ |
| Final | [Date] | ⏳ |
```

---

## Step 4: Create Templates

### Article Template (`templates/article-template.md`)

Only for articles/blog projects:

```markdown
# [Article Title]

**Status**: Draft  
**Created**: [Date]  
**Target Length**: ~[X] words

## TL;DR

[One-paragraph summary]

## Introduction

[Hook the reader — why should they care?]

## Main Content

### [Section 1]

### [Section 2]

### [Section 3]

## Conclusion

[Key takeaways]

## References

- [Source 1]
- [Source 2]

---
*Word count: 0*
```

### Chapter Template (`templates/chapter-template.md`)

Only for book projects:

```markdown
# Chapter N: [Title]

**Status**: Draft  
**Target Length**: ~[X] words

## Chapter Summary

[What the reader will learn in this chapter]

## Content

### [Section 1]

### [Section 2]

## Key Takeaways

- [Takeaway 1]
- [Takeaway 2]

## Exercises / Discussion Questions

1. [Question]

---
*Word count: 0*
```

### Lesson Template (`templates/lesson-template.md`)

Only for course material:

```markdown
# Module N: [Title]

**Status**: Draft  
**Duration**: ~[X] minutes

## Learning Objectives

By the end of this module, the learner will be able to:
1. [Objective 1]
2. [Objective 2]

## Prerequisites

- [Prerequisite 1]

## Lesson Content

### [Topic 1]

### [Topic 2]

## Summary

[Recap of key concepts]

## Next Steps

[What comes next in the course]
```

---

## Step 5: Create First Content File

Based on the project type, create a starter content file:

- **Articles**: `drafts/001-first-article.md` from article template
- **Book**: `chapters/00-introduction.md` from chapter template
- **Course**: `modules/01-getting-started/lesson.md` from lesson template
- **Documentation**: `docs/getting-started.md` with a basic "Getting Started" page

Fill in the title and any structure the user mentioned. Leave the body as placeholder sections for them to fill in.

---

## Step 6: Handoff to Framework Setup

Tell the user:

```
Your content writing project is scaffolded! Here's what's ready:

- outline.md — your overall plan (fill this in first!)
- {{CONTENT_FOLDER}}/ — where your finished content lives
- drafts/ — for work in progress
- assets/ — for images and diagrams
- templates/ — reusable templates for new {{UNIT}}s

Continuing with framework setup...
```

Then return control to `INSTALLATION.md` Step 1 to continue with framework initialization. The project information for Step 1 is:

- **Project Name**: `{{PROJECT_TITLE}}`
- **Project Type**: Content writing project ({{CONTENT_TYPE}})
- **Current Phase**: New — outline and structure created
- **Tech Stack**: Markdown (or chosen format)
- **Primary Language**: Markdown
- **Dev Command**: N/A (or static site generator command if applicable)
- **Test Command**: N/A
- **Build Command**: N/A (or build command for static site / PDF export)
