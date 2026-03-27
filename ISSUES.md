# Seeded Issues

Create these manually in GitHub after pushing the repo.
Copy the title and body for each into GitHub Issues.

---

## Issue 1

**Title:** Add tool profiles for Replit, Framer, and Google Stitch

**Labels:** `enhancement`, `good first issue`

**Body:**
The current tool table covers the most common targets (Cursor, Lovable, v0, Bolt, Figma Make, Claude, ChatGPT, Codex) but misses a few tools with meaningful user bases:

- **Replit** — collaborative, beginner-friendly, full-stack focus
- **Framer** — design-to-publish, strong on interactions and CMS
- **Google Stitch** — prompt-to-UI from Google Labs, Gemini-powered

Each tool needs:
- A row in the tool table with notes on vocabulary and output format expectations
- Any specific constraints worth baking into generated prompts (e.g. Framer's CMS patterns, Replit's deployment model)

If you use any of these tools regularly, you're the right person to add this. See `CONTRIBUTING.md` for how to test and submit.

---

## Issue 2

**Title:** Deep mode Wave 3 stack question is too open-ended

**Labels:** `improvement`

**Body:**
In Deep mode, Wave 3 Question 8 currently asks:

> "What's the tech stack? (framework, component library, styling approach)"

This is too broad and often produces vague answers like "React" with no further detail. The skill then has to make assumptions about component library and styling that may not match what the user actually has.

Proposed improvement: break this into two targeted sub-questions, or provide common stack combinations as examples to anchor the user's answer (e.g. "Next.js + shadcn/ui + Tailwind, plain React + CSS Modules, SvelteKit + UnoCSS, etc.").

Open to other approaches — the goal is getting a complete, usable stack spec without slowing down the wave pacing.

---

## Issue 3

**Title:** Add a "mid-build continuation" mode as a first-class flow

**Labels:** `enhancement`

**Body:**
Currently the skill handles mid-build continuation as an edge case at the bottom of SKILL.md:

> "Ask: 'What's been built so far, and what do you want to add or change?' Then treat the existing work as a constraint in the prompt."

This should be a proper first-class path — something the skill asks about upfront alongside depth/format/tone, or detects automatically when the user's phrasing suggests they're extending something that already exists ("add a sidebar to...", "update the nav to...", "extend this with...").

A good implementation would:
- Detect continuation intent from the trigger phrase
- Ask for a brief description of what exists
- Treat the existing code/design as a constraint block in the generated prompt
- Adjust the interview questions accordingly (skip "what are you building from scratch" type questions)
