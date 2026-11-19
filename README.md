# Agent Skills

A personal collection of reusable [Agent Skills](https://agentskills.io) (`SKILL.md`) that can be installed into any project or agent harness.

## Available Skills

| Skill | Description |
| :--- | :--- |
| [`short`](./skills/short/SKILL.md) | Respond with a 1-word or 1-line answer and no extra explanation (e.g., `/short does this file do X?` → `Yes.`). |

---

## Installing Skills

All skills follow the open `SKILL.md` format, so the same skill folder works across agent harnesses (Gemini CLI, Antigravity, Claude Code, Cursor, Codex CLI, etc.). Only the target install directory differs slightly by harness.

### Option 1: Using the `skills` CLI (Multi-Harness)

Installs into the right directory for your chosen harness(es):

```bash
# Install all skills into the current project
npx skills add ericreinke/skills

# Install a single skill into the current project
npx skills add ericreinke/skills --skill short

# Install globally (available in all projects)
npx skills add ericreinke/skills -g
```

### Option 2: Gemini CLI

```bash
# Install into the current workspace (.gemini/skills/ or .agents/skills/)
gemini skills install https://github.com/ericreinke/skills --scope workspace

# Install globally (~/.gemini/skills/ or ~/.agents/skills/)
gemini skills install https://github.com/ericreinke/skills
```

For local development inside an active Gemini CLI session, you can also link a local folder directly:

```text
/skills link /path/to/skills/skills/short --scope workspace
```

### Option 3: Manual Copy or Symlink (Any Harness)

Clone this repo locally and copy or symlink the skill folder into your project (or global) skills directory:

```bash
# Symlink into a project using the universal .agents/skills/ path
mkdir -p .agents/skills
ln -s /path/to/skills/skills/short .agents/skills/short

# Or copy it if you want to commit it into the project repo
cp -r /path/to/skills/skills/short .agents/skills/short
```

---

## Skill Directories by Harness

Most harnesses have converged on `.agents/skills/` for project-level skills, though global paths and native directories still vary:

| Harness | Project-Local Path | Global Path |
| :--- | :--- | :--- |
| **Universal Standard** | `.agents/skills/<name>/` | `~/.agents/skills/<name>/` |
| **Antigravity** | `.agents/skills/<name>/` | `~/.gemini/config/skills/<name>/` |
| **Gemini CLI** | `.gemini/skills/<name>/` or `.agents/skills/<name>/` | `~/.gemini/skills/<name>/` or `~/.agents/skills/<name>/` |
| **Claude Code** | `.claude/skills/<name>/` | `~/.claude/skills/<name>/` |
| **Cursor** | `.agents/skills/<name>/` or `.cursor/skills/<name>/` | `~/.agents/skills/<name>/` or `~/.cursor/skills/<name>/` |
| **Codex CLI** | `.agents/skills/<name>/` or `.codex/skills/<name>/` | `~/.agents/skills/<name>/` |

> **Tip (Multiple Harnesses):** If you use several harnesses globally (e.g., Claude Code + Gemini CLI + Cursor), keep your skills in `~/.agents/skills/` and symlink tool-specific global directories to it (for example, `ln -s ~/.agents/skills ~/.claude/skills`) so you only install once.

---

## Usage

Once installed, invoke a skill directly with a slash command (in harnesses that support `/skill-name`) or mention it in your prompt:

```text
/short does auth.ts refresh expired tokens?
# → Yes.

/short what table stores invoice line items related to subscriptions?
# → subscription_invoice_items
```
