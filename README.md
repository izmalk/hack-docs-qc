# How-to Auditor

Automated quality checker for How-to Guide documentation. Uses an LLM to evaluate drafts against 26 predefined criteria derived from the Diátaxis framework, producing a structured PASS/FAIL report with rationales for each failure.

## What it does

The auditor verifies that a How-to Guide follows best practices for procedural documentation — correct structure, actionable language, proper formatting, appropriate scope, and completeness. It leverages LLM reasoning to judge compliance rather than relying on simple pattern matching, allowing it to handle nuance and context.

## Repository structure

```
how-to-auditor/          # LLM skill (self-contained, portable)
├── SKILL.md             # Skill definition with full evaluation protocol
├── README.md            # Skill-specific install and usage docs
└── context/
    ├── how-to-criteria-examples.yaml   # 26 criteria with GOOD/BAD examples
    └── diataxis-howto-summary.md       # Diátaxis How-to Guide summary

resources/               # Source materials used to develop the criteria
└── how-to-criteria.md
```

## How to use

### With OpenCode

Copy the skill folder into your project or global skills directory:

```bash
# Project-local (recommended)
cp -r how-to-auditor .opencode/skills/

# Global
cp -r how-to-auditor ~/.config/opencode/skills/
```

The agent will discover it automatically. Submit a How-to Guide draft and ask for a review.

### With any LLM (manual)

1. Load `how-to-auditor/SKILL.md` as the system prompt.
2. Load both files from `how-to-auditor/context/` as additional context.
3. Provide the How-to Guide draft as the user message.
4. Set temperature to 0 for deterministic results.

### With Claude / compatible agents

```bash
cp -r how-to-auditor .claude/skills/
```

## Configuration

| Setting | Value |
|---------|-------|
| Recommended model | DeepSeek v4 Pro |
| Minimum context window | 32K tokens |
| Temperature | 0.0 |
| Interaction mode | Single-turn (stateless) |
