# AI IDE Configuration Templates

These templates help configure AI coding assistants in various AI-powered IDEs to work effectively with your project.

## Available Templates

| File | Purpose | Used By |
|------|---------|---------|
| `CLAUDE.md` | Project instructions for Claude-based AI | Cursor, Claude.ai |
| `context.md` | Project context summary | All AI assistants |
| `.cursorrules` | Cursor-specific AI rules | Cursor IDE |
| `.windsurfrules` | Windsurf-specific AI rules | Windsurf IDE |

## How to Use

### During Framework Installation

When the AI Supervisor-Worker Framework is initialized, these templates are customized based on your project information and placed in your project root.

### Manual Setup

1. Copy the relevant template(s) to your project root
2. Replace all `{{PLACEHOLDER}}` values with your project-specific information
3. Adjust rules to match your coding standards

## Template Placeholders

| Placeholder | Description | Example |
|-------------|-------------|---------|
| `{{PROJECT_NAME}}` | Your project name | "My Web App" |
| `{{PROJECT_TYPE}}` | Type of project | "Next.js Web Application" |
| `{{PROJECT_DESCRIPTION}}` | Brief description | "E-commerce platform with..." |
| `{{TECH_STACK}}` | Main technologies | "TypeScript, Next.js, PostgreSQL" |
| `{{PRIMARY_LANGUAGE}}` | Main programming language | "TypeScript" |
| `{{FRAMEWORK}}` | Main framework | "Next.js 14" |
| `{{TEST_COMMAND}}` | How to run tests | "npm test" |
| `{{DEV_COMMAND}}` | How to start dev server | "npm run dev" |
| `{{CURRENT_DATE}}` | Today's date | "December 4, 2025" |

## File Locations

After installation, files should be placed at:

```
your-project/
├── CLAUDE.md              # Root level for Cursor/Claude
├── context.md             # Root level for context
├── .cursorrules           # Root level for Cursor
├── .windsurfrules         # Root level for Windsurf
└── docs/
    └── SUPERVISOR/        # Framework documents
        └── ...
```

## Customization Tips

### For Web Projects
- Include API routes documentation
- Add frontend/backend separation notes
- Document state management approach

### For Libraries
- Emphasize API stability
- Include versioning rules
- Document public vs internal APIs

### For Microservices
- Document service boundaries
- Include inter-service communication patterns
- Note deployment considerations

## Integration with Framework

These configuration files work alongside the Supervisor-Worker Framework:
- They reference `docs/SUPERVISOR/` for status and tracking
- They instruct AI to follow framework protocols
- They ensure consistent behavior across chat sessions

---

**Version**: 1.0.0  
**Last Updated**: December 2024

