# html-style

A Claude Code skill that gives every HTML page and artifact one calm, consistent look and a plain-English writing style.

See it in use: open `example.html` in a browser.

## Install

```bash
mkdir -p ~/.claude/skills/html-style
curl -o ~/.claude/skills/html-style/SKILL.md https://raw.githubusercontent.com/gayuru/html-style/main/SKILL.md
```

Claude Code loads the skill automatically when it builds an HTML page or artifact.

## What it covers

- design tokens, shadcn-style components (tabs, buttons, badges, cards), and a light/dark icon switch (light by default)
- motion rules: custom easing curves, short transitions, press feedback, fade-and-rise entrances
- writing style: GOV.UK plain English and Simplified Technical English
- UI copy patterns for buttons, success messages, errors, and loading states
