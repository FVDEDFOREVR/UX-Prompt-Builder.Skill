# Contributing to UX Prompt Builder

Thanks for being here. This is a single-file skill — contributions are low-lift and high-impact.

---

## What's worth contributing

- **New tool profiles** — if you use a tool not covered (Replit, Framer, Builder.io, Google Stitch, etc.), add its vocabulary and output format rules to the tool table in SKILL.md
- **Interview question improvements** — better questions for Quick or Deep mode that surface more useful context
- **Stack defaults** — common stack combinations worth recognizing and handling gracefully
- **Edge case handling** — situations the skill doesn't handle well today (see open issues)
- **Output format improvements** — better structured section templates, cleaner single-block patterns

## What to avoid

- Adding complexity that slows down the Quick mode path
- Opinionated design choices that override the user's stated preferences
- Tool-specific rules that are too narrow to be useful to others

---

## How to contribute

1. Fork the repo
2. Make your changes to `SKILL.md`
3. Test it — install the skill in Claude and run through at least one Quick and one Deep intake with your changes
4. Open a PR using the pull request template
5. Describe what you changed and why, and include an example prompt the updated skill produced

---

## Testing your changes

The skill lives entirely in `SKILL.md`. To test:

1. Go to **claude.ai → Settings → Skills**
2. Install your modified version (you may need to remove the existing one first)
3. Start a new chat and trigger it with something like *"I want to build a [component/page/app]"*
4. Run through both Quick and Deep modes
5. Test at least two different target tools and confirm the output vocabulary shifts appropriately

---

## Questions

Open an issue and tag it `question`. Happy to help scope a contribution before you build it.
