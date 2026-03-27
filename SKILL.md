---
name: ux-prompt-builder
description: >
  Guides the user through a structured intake interview to produce a high-quality,
  copy-paste-ready prompt for building UX/UI work in any AI coding or design tool.
  Use this skill whenever the user wants to build a UI, component, page, prototype,
  design system, or any frontend artifact — even if they say "help me write a prompt",
  "I want to build X", "generate a Lovable prompt", "write me a Cursor prompt", or
  just describe a UI idea without a clear next step. Trigger proactively any time the
  user seems to be starting a new build. Covers all targets: Claude, ChatGPT, Codex,
  Cursor, Windsurf, Copilot, Lovable, v0, Bolt, Figma Make, Pencil, and more.
---

# UX Prompt Builder Skill

This skill interviews the user about what they want to build, then outputs a
polished, copy-paste-ready prompt tailored to their chosen AI tool and output style.

---

## Step 1 — Orient the User

Start by presenting three choices up front. Do not ask any build questions yet.

Say something like:

> "Let's build your prompt. First, a few quick setup choices:"

Then ask (in a single message, cleanly formatted):

**A. Interview depth**
- 🚀 **Quick** — 3–5 focused questions, get a prompt fast
- 🔬 **Deep** — Full structured intake: flows, states, edge cases, a11y, animation, data

**B. Output format**
- 📄 **Single block** — One clean copy-paste prompt, nothing extra
- 🗂 **Structured** — Broken into labeled sections (Context / Component Spec / Constraints / Output Format) you can edit before pasting

**C. Prompt tone**
- ⚙️ **Technical** — Precise, implementation-focused (best for Cursor, Codex, Windsurf, Copilot)
- 🎨 **Descriptive** — Intent and experience-driven (best for Lovable, v0, Bolt, Claude, ChatGPT, Figma Make)
- 🔀 **Hybrid** — Both: intent up front, technical constraints at the end

After the user answers A, B, and C — proceed to Step 2.

---

## Step 2 — Identify the Build Target

Ask which tool they're pasting into. This shapes vocabulary, constraints, and formatting.

> "Which tool are you pasting this prompt into?"

Options to offer:
- Claude (new chat)
- ChatGPT
- Codex / OpenAI API
- Cursor
- Windsurf
- GitHub Copilot
- Lovable
- v0 (Vercel)
- Bolt
- Figma Make
- Pencil / Paper / Stitch
- Other (ask them to name it)

**Tool-specific notes to bake into the generated prompt:**

| Tool | Notes |
|---|---|
| Cursor / Windsurf / Copilot | Include file paths, component names, import style. Prefer explicit TypeScript types. |
| Codex / OpenAI API | Be explicit about function signatures, exports, and file structure. No ambiguity. |
| Lovable / Bolt | Describe the full experience. Mention interactivity, transitions, layout intent. |
| v0 | shadcn/ui-first. Mention component names by their shadcn equivalents when possible. |
| Figma Make / Pencil | Focus on visual layout, color, spacing, hierarchy. Less code, more design intent. |
| Claude / ChatGPT | Flexible — match the tone chosen in Step 1C. Include context and constraints. |

---

## Step 3 — The Interview

### 3A. Quick Mode (3–5 questions)

Ask these in a single message, numbered:

1. **What are you building?** (component, page, full app, prototype, design system element — describe it)
2. **What's the core user action or goal?** (what does the user do or get from this?)
3. **What's your tech stack?** (or should I ask? — if they've set defaults, surface them here)
4. **Any specific visual style, design system, or reference?** (e.g., dark editorial, shadcn/ui, brutalist, Material)
5. **Anything this should NOT do, or constraints I should know?** (no animations, accessible only, mobile-first, etc.)

After they answer, go directly to Step 4.

### 3B. Deep Mode (Full Structured Intake)

Ask in grouped waves — do not dump all questions at once. Wait for each group's answers before proceeding.

**Wave 1 — The What**
1. What are you building? (type, name, purpose)
2. Who is the primary user and what's their goal?
3. What problem does this solve or what value does it deliver?

**Wave 2 — The Behavior**
4. What are the key user interactions or flows?
5. What states does this UI have? (empty, loading, error, success, disabled, hover, active, etc.)
6. Does anything animate or transition? If so, describe the feel.
7. Is there any real or mocked data? What shape is it?

**Wave 3 — The Structure**
8. What's the tech stack? (framework, component library, styling approach)
9. Are there existing components, tokens, or patterns this should match or extend?
10. What's the responsive behavior? (mobile-first, breakpoints, fluid, fixed)

**Wave 4 — The Constraints**
11. Accessibility requirements? (WCAG level, keyboard nav, screen reader, color contrast)
12. Performance constraints? (no heavy libraries, lazy load, skeleton states)
13. What should this explicitly NOT do or include?
14. Any references, inspiration, or existing designs to match?

After Wave 4, go to Step 4.

---

## Step 4 — Stack Clarification

Since the skill is set to **always ask about the stack**, after the interview confirm:

> "Quick stack check — what are you working with? (e.g. Next.js + shadcn/ui + Tailwind, plain React + CSS Modules, vanilla HTML/CSS, SvelteKit, etc.)"

If they already answered this in the interview, skip this step.

---

## Step 5 — Generate the Prompt

Use the answers to construct the output based on their format and tone choices.

### Single Block Format

Output one clean, unbroken prompt block inside a code fence (` ```prompt `):

```
Build [what they're building].

[Context and user goal.]

Stack: [their stack]
Style: [visual direction]

[Behavior, states, interactions — written to match chosen tone.]

[Constraints and what to avoid.]

[Output format instruction — e.g., "Return a single React component with no external dependencies" or "Output the full page with Tailwind classes and inline comments."]
```

### Structured Format

Output labeled sections in a code fence:

```
## Context
[What this is, who it's for, what problem it solves]

## Component / Page Spec
[What to build, core interactions, states, data]

## Stack & Style
[Framework, libraries, visual direction, design system]

## Constraints
[What to avoid, accessibility, performance, responsiveness]

## Output Format
[How the AI should respond — file structure, exports, comments, etc.]
```

---

## Step 6 — Tone Pass

Before rendering the final output, apply the tone filter:

**Technical tone** — Rewrite spec language to be precise and implementation-literal:
- Use exact component/prop names
- Specify TypeScript types where relevant
- Name files and exports explicitly
- Avoid adjectives like "sleek" or "smooth" — use specific values (e.g., "200ms ease-in-out transition")

**Descriptive tone** — Rewrite to be experience-first:
- Lead with the user's experience, not the implementation
- Use evocative but grounded language ("feels weightless", "no visible loading flicker")
- Defer technical details to the end or omit unless critical

**Hybrid tone** — Structure as: experience intent (2–3 sentences) → technical spec (bulleted)

---

## Step 7 — Deliver & Offer Next Steps

After outputting the prompt, always offer:

> "This is ready to paste. Want me to:
> - **Refine** any section?
> - **Generate a variant** for a different tool?
> - **Add more detail** on a specific part (states, animation, data, a11y)?
> - **Start a new prompt** for something else?"

---

## Prompt Quality Checklist (internal — do not show to user)

Before outputting, verify the prompt:
- [ ] Has a clear subject (what is being built)
- [ ] States the user goal or context
- [ ] Specifies the stack
- [ ] Includes at least one visual/style direction
- [ ] Mentions key states or interactions (if relevant)
- [ ] Has at least one constraint or "do not"
- [ ] Ends with a clear output format instruction
- [ ] Matches the chosen tone throughout
- [ ] Is written for the specific target tool's expectations

If any item is missing and the user didn't address it, either infer it clearly or ask a single targeted follow-up before generating.

---

## Edge Cases

**User skips the interview and just describes what they want in their first message:**
Extract as much as you can from their description, surface any missing checklist items as a short "just confirming a few things" check (max 3 questions), then generate.

**User says "just generate it":**
Use whatever you have. Note any assumptions made at the top of the output in italics, then show the prompt.

**User wants multiple tool variants:**
Generate each in its own labeled block. Keep context shared, but adjust vocabulary, constraints, and output format instructions per tool.

**User is mid-build and wants a prompt to continue or extend:**
Ask: "What's been built so far, and what do you want to add or change?" Then treat the existing code/design as a constraint in the prompt.
