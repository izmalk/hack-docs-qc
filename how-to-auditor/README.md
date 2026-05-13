# How-to Auditor — LLM Skill

An LLM skill that audits How-to guides against 26 criteria derived from the Diátaxis framework, producing a structured PASS/FAIL report.

## Contents

```
how-to-auditor/
├── SKILL.md             # Skill definition (frontmatter + evaluation protocol)
├── README.md            # This file
└── context/
    ├── how-to-criteria-examples.yaml   # 26 criteria with GOOD/BAD examples
    └── diataxis-howto-summary.md       # Diátaxis How-to Guide summary
```

## Installation

Copy the skill folder into one of the supported locations:

```bash
# OpenCode — project-local (recommended)
cp -r how-to-auditor .agents/skills/

# OpenCode — global
cp -r how-to-auditor ~/.config/opencode/skills/

# Claude-compatible
cp -r how-to-auditor .claude/skills/
```

The skill name `how-to-auditor` matches the required pattern `^[a-z0-9]+(-[a-z0-9]+)*$`.

## Usage

**With an agent (OpenCode, Claude, etc.):**
The skill is automatically discovered once installed. Ask the agent to review a How-to guide and it will load the skill and apply all 26 criteria.

**Manual use (raw LLM API):**
1. Load `SKILL.md` (below the frontmatter `---`) as the system prompt.
2. Load both files from `context/` as additional context.
3. Provide the How-to guide draft as the user message.
4. Set `temperature=0` for deterministic output.

**Expected output:**
- Summary (total passed/failed).
- For each failure: full criterion text, rationale, and quoted evidence.
- Human Verification Warning at the end.

## Packaging for distribution

```bash
cd how-to-auditor
zip -r ../how-to-auditor-v1.0.0.zip .
```

## Criteria

See `context/how-to-criteria-examples.yaml` for the full list of 26 criteria (C01–C10 common, H01–H16 how-to specific) with concrete GOOD/BAD examples.

## Configuration

| Setting | Value |
|---------|-------|
| Recommended model | DeepSeek v4 Pro |
| Minimum context window | 32K tokens |
| Temperature | 0.0 |
| Interaction mode | Single-turn (stateless) |

## License

GPL-3.0
