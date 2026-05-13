# How-to Auditor

This is the How-to Auditor project from Canonical's Engineering sprint Hackathon at Madrid 2026.

Automated quality checker for How-to guides that verifies a static set of criteria. Uses an LLM to evaluate guides against 26 predefined criteria derived from the Diátaxis framework and other best practices, producing a structured PASS/FAIL report.

Tested and created with Open Code and Open Router, using DeepSeek V4 Pro model.

## What it does

The auditor verifies that a How-to Guide follows best practices — correct structure, actionable language, proper formatting, appropriate scope, and completeness. It leverages LLM reasoning to judge compliance rather than relying on simple pattern matching, allowing it to handle nuance and context.

## Repository structure

```
how-to-auditor/          # LLM skill (self-contained, portable)
├── SKILL.md             # Skill definition with full evaluation protocol
├── README.md            # Skill-specific install and usage docs
└── context/
    ├── how-to-criteria-examples.yaml   # 26 criteria with GOOD/BAD examples
    └── diataxis-howto-summary.md       # Diátaxis How-to Guide summary
```

## How to use

Copy the skill folder into your project or global skills directory:

```bash
cp -r how-to-auditor .agents/skills/
```

Make sure to activate/enable the skill in your tool of choice.
For example, run `opencode` and then `/skills` in the folder with `.agents` in it.

Finally, asl LLM to verify a particular guide that it can access via file operation, in a prompt, remotely address, etc.

## Configuration

| Setting | Value |
|---------|-------|
| Recommended model | DeepSeek v4 Pro |
| Minimum context window | 32K tokens |
| Temperature | 0.0 |
| Interaction mode | Single-turn (stateless) |
