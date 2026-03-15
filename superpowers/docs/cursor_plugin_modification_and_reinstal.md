# Plugin modification and reinstallation
_Exported on 3/14/2026 at 10:06:13 CDT from Cursor (2.6.19)_

---

**User**

This project is  clone of https://github.com/obra/superpowers 
which is a plugin for cloud or cursor.

Please become familliar with it because I have some questions.

If I make some local changes to this plugin, for example i bring some features from my Supervisor project (https://github.com/PREDICTif/supervisor-worker-ai-framework ) how would I re-install the modified version?

---

**Cursor**

Let me explore the local workspace structure to understand how this plugin is set up.

Now I have a complete picture of the setup. Let me summarize what I found and answer your question.

---

## How the Superpowers Plugin Works in Cursor

### How Cursor Stores Plugins

Cursor has two plugin storage locations:
- **`~/.cursor/plugins/cache/cursor-public/<name>/<commit-hash>/`** — plugins installed from the marketplace (git clones at a specific commit)
- **`~/.cursor/plugins/local/`** — for locally installed plugins (currently empty on your machine)

The superpowers plugin is **not yet installed** in Cursor — your workspace at `/Users/marian.dumitrascu/___1/work-P/superpowers/` is just the cloned source repo.

---

## Options for Installing Your Modified Version

### Option 1: Symlink into the local plugins directory (recommended for development)

This lets you edit files in your workspace and have Cursor pick up changes immediately:

```bash
mkdir -p ~/.cursor/plugins/local/superpowers
# Symlink the plugin definition and content from your local repo
ln -s /Users/marian.dumitrascu/___1/work-P/superpowers/.cursor-plugin/plugin.json \
      ~/.cursor/plugins/local/superpowers/
```

Or symlink the entire directory:

```bash
ln -s /Users/marian.dumitrascu/___1/work-P/superpowers \
      ~/.cursor/plugins/local/superpowers
```

Then restart Cursor and run `/add-plugin superpowers` pointing at your local path, or check if Cursor auto-discovers the `local/` folder.

### Option 2: Edit the cache directly (after a normal install)

1. First install the official version: `/add-plugin superpowers` in Cursor Agent chat
2. This creates `~/.cursor/plugins/cache/cursor-public/superpowers/<commit-hash>/`
3. Edit files directly in that directory — your changes take effect on next session

The downside: Cursor may overwrite these on `/plugin update superpowers`.

### Option 3: Push to a GitHub fork (cleanest for sharing)

1. Push your local changes to a fork (e.g., `github.com/marian-dumitrascu/superpowers`)
2. Cursor supports installing from custom repos — you can use the plugin marketplace mechanism pointing at your fork

---

## Practical Recommendation

For **iterative development** (adding Supervisor features), the workflow would be:

1. Make changes in your local repo (`/Users/marian.dumitrascu/___1/work-P/superpowers/`)
2. Add new skills as `SKILL.md` files under `skills/<your-skill-name>/SKILL.md` following the existing pattern
3. Sync to `~/.cursor/plugins/local/superpowers/` via symlink or copy
4. Restart Cursor

Would you like me to help you create a new skill based on the Supervisor-Worker framework patterns, or set up the symlink-based local install workflow?

---

**User**

Can you give me some idea of how can i incorporate Supervisor into Superpower, or how can I bring Superpowers into Supervisor. I like with supervisor that is easy to install I just copy paste:
"
Initialize the supervisor-worker AI framework from:
https://github.com/PREDICTif/supervisor-worker-ai-framework

Create the framework in ./docs/SUPERVISOR/ folder.
"

---

**Cursor**

I’m mapping the easiest integration paths between the two projects and checking how Superpowers currently boots itself so I can suggest concrete options instead of abstract ideas.

I’ve confirmed Superpowers is basically a skill-pack plus a session-start bootstrap, so the cleanest integration point is either the bootstrap prompt or a generated local skill bundle. I’m reading those pieces now.

The repo confirms Superpowers is mostly a skill loader plus a startup hook, so adding Supervisor on the Superpowers side would mainly mean adding new skills, commands, and maybe a small scaffold step rather than rewriting core behavior.

After looking at `.cursor-plugin/plugin.json` and `hooks/session-start`, I’d treat [Superpowers](https://github.com/obra/superpowers) and [supervisor-worker-ai-framework](https://github.com/PREDICTif/supervisor-worker-ai-framework) as two different layers:

- `Superpowers` = global reusable process engine: skills, startup bootstrap, workflow discipline.
- `Supervisor` = project-local operating system: roles, handoff docs, delegation tracker, current status.

Because you like the simple install prompt, I’d recommend **bringing Superpowers into Supervisor**, not the reverse.

## Recommended Direction

Keep the current Supervisor init prompt as the front door, and make it generate a small bridge to Superpowers concepts.

That means your Supervisor install would still create `docs/SUPERVISOR/`, but also add one local instruction file such as `AGENTS.md` or a Cursor rule that says:

- use Superpowers-style brainstorming before implementation
- use planning before coding
- use TDD for implementation
- use debugging workflow for bugs
- use review + verification before closing work

A thin mapping file like `docs/SUPERVISOR/SUPERPOWERS-BRIDGE.md` could map:

- planning -> `brainstorming`, `writing-plans`
- execution -> `subagent-driven-development`
- debugging -> `systematic-debugging`
- review -> `requesting-code-review`
- final checks -> `verification-before-completion`

That preserves your easy copy-paste install, and if the plugin is installed later, the project is already aligned with it.

## If You Want The Other Direction

If you want to put Supervisor inside Superpowers, I would do it as **new skills plus templates**, not as big hook logic.

Add skills like:

- `supervisor-init`
- `supervisor-role`
- `worker-role`
- `delegation-handover`
- `status-update`

Then let one of those scaffold `docs/SUPERVISOR/` into the project. Since Superpowers is already centered on `skills/`, that is the natural extension point. I would avoid packing the whole Supervisor framework into `hooks/session-start`; keep the hook small and let it point to skills.

## Best Hybrid

The cleanest hybrid is:

- `Supervisor` owns project memory and role scaffolding.
- `Superpowers` owns execution methodology.

So the user experience becomes:

```text
Initialize the supervisor-worker AI framework from:
https://github.com/PREDICTif/supervisor-worker-ai-framework

Create the framework in ./docs/SUPERVISOR/ folder.

If Superpowers is available, use it as the default execution methodology for planning, TDD, debugging, code review, and verification.
If Superpowers is not available, create local project instructions that emulate those workflows.
```

That gives you the simple install you like, without forcing plugin installation first.

If you want, I can next sketch the exact file layout for this hybrid: which `skills/` to add in Superpowers, or which `AGENTS.md` / rule files to generate from Supervisor.

---

**User**

Can I add supepowers to Supervisor, and when I say "Initialize the supervisor-worker AI framework from:
https://github.com/PREDICTif/supervisor-worker-ai-framework". it will also install superpowers from a repo subfolder, for the respective project that I am working on?

---

**Cursor**

I’m checking the boundary between “project initialization” and “plugin installation,” because that’s the key limitation here: Supervisor can definitely scaffold project files, but Cursor plugin install itself is handled differently.

Yes, but with one important caveat:

**Supervisor can initialize project-local files. Superpowers as a Cursor plugin is machine-global, not naturally project-local.**

So the answer is:

- `Yes` if you mean: "Initialize Supervisor and also set up Superpowers-style behavior for this project."
- `Not cleanly` if you mean: "Every project gets its own private Cursor plugin installed from a subfolder automatically."

## What I’d recommend

Use a **2-layer model**:

- **Global layer**: install your forked Superpowers once on your machine.
- **Project layer**: let Supervisor scaffold project-specific rules, status files, delegation docs, and handoff workflow.

That gives you the simple Supervisor install UX you like, while avoiding plugin reinstallation every time you start a new project.

## Why per-project plugin install is awkward

From what I inspected locally, Superpowers is packaged as a Cursor plugin via `.cursor-plugin/plugin.json`, and Cursor keeps plugins under `~/.cursor/plugins/...`, which is outside the project. That means:

- plugin install is effectively **user-machine scoped**
- project init can create symlinks or copy files there
- but that is still **not really per-project**
- switching between projects with different plugin variants becomes messy

So if you vendored Superpowers inside Supervisor like:

```text
supervisor-worker-ai-framework/
  vendor/superpowers/
```

your init prompt could create a symlink from that vendored copy into `~/.cursor/plugins/local/...`, but that would still be a machine-level plugin install, and usually requires restarting Cursor.

## Best architecture

### Option A: Best overall
Fork [Superpowers](https://github.com/obra/superpowers) into your own repo, add your Supervisor-oriented changes there, install that fork once, and let [Supervisor](https://github.com/PREDICTif/supervisor-worker-ai-framework) remain the easy per-project initializer.

Then your prompt stays simple:

```text
Initialize the supervisor-worker AI framework from:
https://github.com/PREDICTif/supervisor-worker-ai-framework

Create the framework in ./docs/SUPERVISOR/ folder.

Assume my custom Superpowers fork is already installed and use it as the execution methodology.
```

### Option B: Hybrid bootstrap
Keep Supervisor as the entrypoint, and during init have it:

1. Create `docs/SUPERVISOR/`
2. Detect whether your custom Superpowers is installed
3. If installed, use it
4. If not installed, generate project-local fallback instructions that emulate Superpowers workflows

This is the most robust pattern.

### Option C: Full auto-link from vendored subfolder
Possible, but less clean:

1. Vendor Superpowers inside Supervisor
2. On init, run a shell script that links that vendored folder into `~/.cursor/plugins/local/your-plugin`
3. Ask for Cursor restart

This works technically, but I would only use it for your own machine, not as the primary design.

## My practical recommendation

If your goal is **easy installation**, do this:

- keep Supervisor as the copy-paste initializer
- keep Superpowers as a separate reusable engine
- let Supervisor generate project-local instructions that *call into* Superpowers when available
- only install your custom Superpowers fork once per machine

In other words: **project-specific behavior belongs in Supervisor; reusable methodology belongs in Superpowers.**

If you want, I can sketch the exact setup for this:
- `Supervisor + global custom Superpowers`
- `Supervisor that auto-detects and falls back`
- `Supervisor that links a vendored Superpowers subfolder into Cursor local plugins`

