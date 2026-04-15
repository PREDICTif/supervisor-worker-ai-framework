# Study Project Scaffolding Template

**For AI Assistants**: Follow these instructions to scaffold a multi-part study project in an empty folder. This project type is for learning a subject by building several small, self-contained demos or experiments inside one repository.

---

## Step 1: Ask Follow-Up Questions

Before scaffolding, ask the user:

```
Great — a multi-part study project! A few quick questions:

1. **What subject are you studying?** (e.g., "Rust concurrency", "LLM agents", "System design patterns")
2. **Preferred language(s)?** (e.g., Python, TypeScript, Go — or "mixed" if each part may differ)
3. **Project name?** (default: derived from subject, e.g., "rust-concurrency-study")
```

Use the answers to fill in the structure below. If the user wants to move fast, derive sensible defaults from the subject.

---

## Step 2: Create Project Structure

```
{project_root}/
├── README.md
├── .gitignore
└── part-01-getting-started/
    └── README.md
```

### README.md (root)

Create a root `README.md` with:

```markdown
# {{PROJECT_NAME}}

Study project: **{{SUBJECT}}**

## Parts

| # | Topic | Status |
|---|-------|--------|
| 01 | Getting Started | 🚧 In Progress |

## How This Repo Works

Each `part-NN-<name>/` folder is a self-contained mini-project with its own dependencies and build steps. See each part's README for instructions.

## Adding a New Part

Create a new folder following the naming convention `part-NN-<short-name>/` and add a README.md inside it explaining what the part covers and how to run it.
```

### .gitignore

Create a `.gitignore` appropriate for the chosen language(s). If the user said "mixed" or didn't specify, use a broad default:

```gitignore
# OS files
.DS_Store
Thumbs.db

# Editor files
.vscode/
.idea/
*.swp
*.swo

# Common build artifacts
node_modules/
__pycache__/
*.pyc
.env
dist/
build/
target/
```

### part-01-getting-started/README.md

Create the first part as a placeholder:

```markdown
# Part 01: Getting Started

## Goal

[Describe what this first experiment explores]

## Setup

```bash
# Add setup commands here
```

## Notes

[Add observations, learnings, links to resources]
```

---

## Step 3: Language-Specific Extras

If the user specified a primary language, add starter files to `part-01-getting-started/`:

**Python:**
- `requirements.txt` (empty or with common study deps like `requests`, `rich`)
- `main.py` with a minimal hello-world

**JavaScript/TypeScript:**
- `package.json` with `name`, `version`, `type: "module"`
- `index.js` or `index.ts` with a minimal hello-world
- If TypeScript: `tsconfig.json`

**Go:**
- `go.mod` with module name
- `main.go` with a minimal hello-world

**Rust:**
- Run `cargo init` inside the part folder (or create `Cargo.toml` + `src/main.rs`)

**Other / Mixed:**
- No language-specific files; the user will add them per-part as needed

---

## Step 4: Convention Notes

Tell the user:

```
Your study project is ready! Here's how it works:

- Each part lives in its own `part-NN-<name>/` folder
- Parts are self-contained — each can have different languages, deps, or frameworks
- The root README tracks all parts with a status table
- When you start a new part, I can scaffold it for you — just say "create part 02: <topic>"

Continuing with framework setup...
```

Then return control to `INSTALLATION.md` Step 1 to continue with framework initialization. The project information for Step 1 is:

- **Project Name**: `{{PROJECT_NAME}}`
- **Project Type**: Multi-part study project
- **Current Phase**: New — Part 01 in progress
- **Tech Stack**: `{{LANGUAGE(S)}}` (or "mixed")
- **Primary Language**: `{{PRIMARY_LANGUAGE}}` (or the first language mentioned)
- **Key Commands**: Vary per part — see each part's README
