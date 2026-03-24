# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [Unreleased]

---

## [1.3.1] - March 14, 2026

### Added
- **March 14, 2026**: `init-supervisor` skill — a bootstrap skill that initializes or re-initializes a Supervisor session
  - Detects whether the framework is already installed (re-init) or needs fresh setup
  - For existing projects: reads framework docs, status, tracker, and logs, then presents a situational briefing
  - For new projects: delegates to INSTALLATION.md for full setup, then presents briefing
  - Added to INSTALLATION.md directory structure, skills copy table, and confirmation section
  - Added to `superpowers-methodology.md` bridge rule (available skills, priority, and activity mapping)
  - Added to SUPERVISOR-FRAMEWORK.md methodology skills reference
  - Added to README.md skills table and directory tree

---

## [1.3.0] - March 14, 2026

### Added
- **March 14, 2026**: Superpowers methodology skills integration
  - Vendored [Superpowers](https://github.com/obra/superpowers) (MIT, by Jesse Vincent) into `superpowers/` subfolder
  - Skills are installed as project-level Cursor skills (`.cursor/skills/`) during framework initialization — no plugin install or IDE restart needed
  - 6 curated methodology skills included: brainstorming, writing-plans, test-driven-development, systematic-debugging, requesting-code-review, verification-before-completion
  - 4 skills evaluated and excluded (redundant with Supervisor framework or platform-coupled): executing-plans, subagent-driven-development, finishing-a-development-branch, dispatching-parallel-agents
  - Created `templates/cursor-rules/superpowers-methodology.md` bridge rule template that maps Supervisor workflows to methodology skills
  - Updated INSTALLATION.md with new Step 3.5 for skill installation and supporting file copy instructions
  - Updated SUPERVISOR-FRAMEWORK.md with methodology skills reference section and skill-guided session workflow
  - Updated README.md with new directory structure, skills table, and Superpowers attribution

### Changed
- **Version**: Updated from 1.2.0 to 1.3.0 across all framework documents
- **INSTALLATION.md**: Directory structure now includes `.cursor/skills/` and `.cursor/rules/`; confirmation template lists installed skills
- **SUPERVISOR-FRAMEWORK.md**: "During Session" workflow now references specific skills at each step; added "Methodology Skills Reference" section
- **README.md**: Framework contents diagram includes `superpowers/` and `templates/cursor-rules/`; AI assistant init steps include skill installation

---

## [1.2.0] - December 31, 2025

### Added
- **December 31, 2025**: Encore Loyalty AI Feedback System case study added to examples
  - Added comprehensive real-world example to `examples/README.md`
  - Documented 11-phase development lifecycle with 25+ worker prompts
  - Included sample CLAUDE.md, worker prompts, and completion reports
  - Added key metrics: 61,803 feedback items, 44+ API endpoints, 98% completion
  - Documented lessons learned and success factors

- **December 31, 2025**: Framework improvements merged from `./framework`
  - Enhanced SUPERVISOR-FRAMEWORK.md with v1.2.0 features
  - Enhanced WORKER-FRAMEWORK.md with success criteria templates
  - Enhanced BEST-PRACTICES.md with comprehensive testing strategy
  - Added new templates: HANDOVER-TEMPLATE.md, BUG-FIX-TEMPLATE.md, PROMPT-TRACKER.md, EMERGENCY-PROTOCOL.md

### New Features in v1.2.0

#### SUPERVISOR-FRAMEWORK.md
- **Supervisor Modes**: Clarified Pure, Hybrid, and Worker modes with clear usage guidelines
- **Bug Management Protocol**: Structured workflow for bug discovery, documentation, and prevention
- **Prompt Execution Tracking**: System for cataloging and tracking task prompts with adaptation handling
- **Status Update Triggers**: Clear rules for when to update documentation
- **Health Score Calculation**: Objective project health assessment methodology

#### WORKER-FRAMEWORK.md
- **Success Criteria Templates**: Task-specific completion checklists for 7 common task types:
  - Feature Implementation
  - Bug Fix
  - Testing Task
  - Documentation Task
  - Refactoring Task
  - Integration Task
  - Configuration/Setup Task

#### BEST-PRACTICES.md
- **Testing Strategy**: Comprehensive testing guidance including:
  - Test ownership clarification (who tests what)
  - Test-driven delegation approach
  - Test failure protocols for both workers and supervisors
  - Coverage guidelines and targets by code type
  - Test report templates
  - Testing phases (development, completion, validation)

#### New Templates
- `HANDOVER-TEMPLATE.md`: Comprehensive session handover guide
- `BUG-FIX-TEMPLATE.md`: Detailed bug documentation template with root cause analysis
- `PROMPT-TRACKER.md`: Task/prompt execution tracking with priority system
- `EMERGENCY-PROTOCOL.md`: Crisis response procedures for critical bugs

### Changed
- **Version**: Updated from 1.1.0 to 1.2.0 across all framework documents
- **Documentation**: Enhanced session end checklists in SUPERVISOR-FRAMEWORK.md
- **Quality**: Better deliverable verification standards in WORKER-FRAMEWORK.md

---

## [1.1.0] - December 4, 2025

### Added
- **December 4, 2025**: AI IDE configuration templates
  - Created `templates/ai-ide-configs/CLAUDE.md` - Claude/Anthropic instructions template
  - Created `templates/ai-ide-configs/context.md` - Project context template
  - Created `templates/ai-ide-configs/.cursorrules` - Cursor IDE rules template
  - Created `templates/ai-ide-configs/.windsurfrules` - Windsurf IDE rules template
  - Created `templates/ai-ide-configs/README.md` - Documentation for AI IDE configs
  - Framework now generates AI IDE config files during initialization

### Changed
- **December 4, 2025**: Clarified framework purpose in README.md
  - Added prominent notice that this is a methodology for AI IDEs, not a library for building AI agents
  - Added "Who Is This For?" section with clear target audience
  - Added "Supported AI IDEs" table (Cursor, Windsurf, Cline, etc.)
  - Updated architecture diagram to show AI chat sessions
  - Updated workflow description to clarify multi-chat pattern
  
- **December 4, 2025**: Enhanced INSTALLATION.md
  - Added Step 3 for generating AI IDE configuration files
  - Added detailed instructions for detecting project information
  - Added guidance on customizing AI IDE configs for different project types
  - Updated confirmation message to include AI IDE config files

---

## [1.0.0] - December 4, 2025

### Added
- Initial release of AI Supervisor-Worker Framework
- Initialized framework in `docs/SUPERVISOR/`
  - Created `SUPERVISOR-FRAMEWORK.md` - Complete supervisor guide
  - Created `WORKER-FRAMEWORK.md` - Complete worker guide
  - Created `BEST-PRACTICES.md` - Tips, patterns, and anti-patterns
  - Created `CURRENT-STATUS.md` - Project health dashboard
  - Created `DELEGATION-TRACKER.md` - Task delegation tracking
  - Created `THINKING-LOG.md` - Strategic decisions log
  - Created `DECISIONS-LOG.md` - Technical decisions log (ADR format)
  - Created `SESSION-SUMMARIES/` directory with session template
