# UX Prompt Builder

A Claude skill that interviews you about what you want to build, then outputs a polished, copy-paste-ready prompt tailored to your target AI tool.

Built by [Daniel Hairston](https://danielhairston.com)

---

## The problem

Every AI builder tool — Lovable, v0, Cursor, Bolt, Figma Make, ChatGPT, Claude — drops you into a blank input and waits. No intake. No brief. No structure.

So you type something vague, get a mediocre result, and spend 40 minutes re-prompting what should have taken five. That's not a model problem. It's a prompt problem.

This skill is the intake layer they all skipped.

---

## What it does

Before asking a single build question, it asks you three things:

- **Depth** — Quick 3–5 questions, or a full structured intake with flows, states, edge cases, a11y, and data
- **Format** — Single copy-paste block, or labeled sections (Context / Spec / Constraints / Output Format) you can edit before pasting
- **Tone** — Technical for Cursor/Codex, descriptive for Lovable/v0/Claude, or hybrid

Then it interviews you, checks your stack, and generates a prompt shaped for the specific tool you're pasting into. Cursor prompts read like engineering specs. Lovable prompts read like product briefs. Same idea, completely different output.

---

## Supported tools

Claude · ChatGPT · Codex · Cursor · Windsurf · GitHub Copilot · Lovable · v0 · Bolt · Figma Make · Pencil · Paper · Google Stitch · and more

---

## Installation

### Option 1 — Install the `.skill` file (recommended)

1. Download `ux-prompt-builder.skill` from this repo
2. Go to **claude.ai → Settings → Skills**
3. Upload the `.skill` file
4. Start a new chat and say anything like:
   - *"I want to build a dashboard"*
   - *"Help me write a Lovable prompt for a card component"*
   - *"I need a Cursor prompt for a sidebar nav"*

The skill should triggers automatically at first. If not, ask Claude if it's using the UX prompt builder skill, it will continue to use that skill across chats after initializing.

### Option 2 — Use the SKILL.md directly

If you're running Claude Code or building your own skill setup, copy `SKILL.md` into your skills directory.

---

## Example

**Input:** `"I want to build a landing page for a music artist"`

**What happens:**
- Skill triggers immediately, reads your context
- Asks depth / format / tone preferences
- Runs a 5-question interview (answered in one line)
- Returns a full, tool-specific prompt in under 2 minutes

**Output (pasted into Claude):** A complete Phantogram landing page — deep navy, Cormorant Garamond serif dissolving into Share Tech Mono, scroll-triggered reveals, a custom cursor — first pass, no correction loop.

---

## The output is a starting point, not a finish line

A well-structured prompt gets you to a real first draft — something with bones, intent, and a point of view. From there you iterate: refine in Claude, pull into Figma, tighten spacing and type, make the decisions that require a designer's eye.

The prompt doesn't replace the craft. It compresses the gap between blank canvas and something worth reacting to.

---

## Forking and extending

The skill is a single `SKILL.md` file — plain markdown with a YAML frontmatter block. Fork it, modify the interview questions, add your own stack defaults, or extend the tool-specific output rules.

Check the Issues tab for specific improvements and entry points.

Even small improvements to prompt structure, interview questions, or tool-specific behavior are valuable.

---

## License

MIT — use it, fork it, build on it.
