# Obsidian + Claude Code: Executive Coaching System Templates

A set of templates for building an AI-native executive coaching system using [Obsidian](https://obsidian.md/) and [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

**Read the full writeup:** [Obsidian + Claude Code: Building an AI-Native Executive Coaching System](https://www.linkedin.com/pulse/obsidian-claude-code-building-ai-native-executive-coaching-crooks-3ixhc) on LinkedIn.

## What is this?

An Obsidian vault structure + Claude Code configuration that turns Claude into a persistent executive coach. It manages projects, runs daily check-ins, tracks patterns, and handles all the bookkeeping — using plain markdown files as the shared source of truth. [Read the full write-up.]()

## Files

| Template | What it does |
|----------|-------------|
| `CLAUDE.md` | The core configuration file. Defines coaching principles, session types (daily check-in, deep dive, weekly review, monthly narrative), file update rules, and vault structure. Drop this in your vault root. |
| `Dashboard.md` | Master index of all active projects with one-line statuses, coaching patterns, and paused/someday lists. Claude reads this every session to get oriented. |
| `Project.md` | One file per active project. Tracks status, blockers, next actions, session log, and retro. |
| `Daily Note.md` | Daily note template with weather, calendar, to-dos, gratitudes, and "make tomorrow easier" section. Claude fills most of this in during check-ins. |
| `Weekly Note.md` | Weekly note with priorities, suggested schedule, check-in log, and weekly review section. The check-in log is the system's memory of what happened each day. |
| `Coaching Context.md` | How you work — energy patterns, what blocks you, what helps, accountability preferences. Claude reads this to calibrate its style. |
| `Claude to Claude.md` | Handoff notes between Claude instances. Bridges the context gap across machines, sessions, compactions, or even different users' Claude instances. |
| `Prompt Doc.md` | Template for building reusable prompt documents — structured instructions that any Claude instance can follow to produce consistent output. |

## Getting started

1. **Install [Obsidian](https://obsidian.md/)** and create a vault (or use an existing one).
2. **Install [Claude Code](https://docs.anthropic.com/en/docs/claude-code/overview)** — see Anthropic's install guide for your platform.
3. **Copy `CLAUDE.md` to your vault root** and customize it — replace `{{name}}`, adjust coaching principles to fit how you work, modify the vault structure to match yours.
4. **Copy `Dashboard.md` to your vault** and fill in your life context and active projects.
5. **Copy the other templates** into a Templates folder in your vault.
6. **Fill in `Coaching Context.md`** — this is where you teach Claude how you work. Be honest about what blocks you and what helps.
7. **Run Claude Code from your vault root** and say "check in."

## How it works

You run Claude Code from your vault's root folder — it's a CLI tool that operates in whatever directory you launch it from. This means Claude has direct read/write access to every file in your vault. The `CLAUDE.md` file (which Claude Code automatically reads on startup) tells it what files to read at the start of each session and how to behave. Over time, the vault accumulates context: check-in logs, project histories, coaching patterns, session artifacts. Claude gets better because the context gets better.

Key concepts:
- **The vault is the source of truth.** Both you and Claude read and write the same files. No black box. Claude Code has a built-in memory system (a hidden dot folder), but this system intentionally redirects all context into the vault instead — coaching files, project files, the dashboard, weekly notes. Everything Claude knows is visible, editable, and shared across instances.
- **Session types structure the interaction.** "Check in" triggers a daily review. "Let's dig into X" triggers a deep dive. "Weekly review" triggers a full retrospective and preview.
- **Coaching patterns emerge over time.** Claude reviews the last 7-10 check-in entries and surfaces trends — what's sticking, what keeps getting punted, where energy mismatches are happening.
- **Prompt docs make tasks repeatable.** Instead of re-explaining complex tasks, write a prompt doc once and reuse it across sessions or Claude instances.
- **Handoff notes** preserve context across machines, sessions, compactions, or even different people's Claude instances. Context resets every conversation — the handoff file is how nothing gets lost.

## Customization

This system was built for one person's brain. Your version should be built for yours. Some things to consider:

- **Coaching principles:** The ones in the template are ADHD-informed (activation energy, time-boxing, scope control). Adjust for what actually works for you.
- **Daily basics:** The daily note tracks meds, exercise, and brushing teeth. Replace with whatever recurring habits you're building.
- **Session types:** Add your own. Maybe you need a "pre-meeting prep" session or a "end of sprint" review.
- **Vault structure:** The template suggests a structure, but Claude Code works with any folder layout. Just update the paths in `CLAUDE.md`.
- **Gratitudes:** Optional but research-backed. Three specific things beats vague positivity ([Emmons & McCullough, 2003](https://doi.org/10.1037/0022-3514.84.2.377)).

## Plugins that pair well

- **[Obsidian Tasks](https://publish.obsidian.md/tasks/)** — dynamic task queries across the vault. Claude can write tasks in the right syntax so queries find them.
- **[Dataview](https://blacksmithgu.github.io/obsidian-dataview/)** — query frontmatter and metadata. Useful for project dashboards.
- **[Templater](https://silentvoid13.github.io/Templater/)** — auto-apply templates when creating new notes.

## Tips & tricks

- **Watch your context usage.** Claude Code has a finite context window (~200k tokens). If Claude starts running slow or forgetting things mid-session, run `/context` in the CLI to check usage. Once you're at 50-60%, it's time to wrap up — make sure all logs, project updates, and handoff notes are written to files, then compact or start a fresh session. The system is designed for this: because everything important gets persisted to files, you lose nothing when the conversation resets.
- **Log before you go.** Before ending or compacting a session, make sure check-in logs, project updates, and handoff notes are written. Future sessions (and future Claude instances) can only know what's in the files.
- **Start small.** You don't need 200 files to begin. A `CLAUDE.md`, a Dashboard, and a daily note template are enough. The system grows organically as you add projects and context.
- **Iterate the `CLAUDE.md` relentlessly.** Every time Claude does something wrong or misses a step, that's a signal to update the spec. The file should evolve constantly in the early weeks.
- **Don't fight the personality.** If you use the system long enough, Claude will develop a working style shaped by your feedback and context. That's a feature, not a bug.

## Philosophy

The hard part isn't prompting. It's **context architecture** — designing what Claude reads, when, and why. A `CLAUDE.md` that's too long wastes context. Too short and Claude forgets how you work. Every rule in the template has a scar behind it: a missed gratitude review, an unfiled daily note, a session that ended without updating the project file.

The system works because markdown is the perfect AI substrate. Obsidian doesn't care who writes the files. Claude doesn't care who reads them. The result is a shared workspace where human and AI build on each other's work, in plain text, with full transparency.
