# Diátaxis How-to Guide Reviewer — OpenCode Skill

A static agent skill that audits How-to Guide documentation drafts against the Diátaxis framework using 26 predefined verification criteria.

## Package Contents

```
diataxis-howto-reviewer/
├── SKILL.md                              # Skill definition (frontmatter + instructions)
├── README.md                             # This file
└── context/
    ├── how-to-criteria-examples.yaml     # 26 verification criteria with GOOD/BAD examples
    └── diataxis-howto-summary.md         # Diátaxis How-to Guide summary
```

## How to Install (OpenCode)

Copy this directory into one of the following locations so OpenCode discovers it:

```bash
# Project-local (recommended)
cp -r diataxis-howto-reviewer .opencode/skills/

# Global
cp -r diataxis-howto-reviewer ~/.config/opencode/skills/

# Claude-compatible
cp -r diataxis-howto-reviewer .claude/skills/
```

The skill name `diataxis-howto-reviewer` matches `^[a-z0-9]+(-[a-z0-9]+)*$` and the containing directory name.

## How to Package (ZIP Distribution)

```bash
cd diataxis-howto-reviewer
zip -r ../diataxis-howto-reviewer-v1.0.0.zip .
```

The ZIP contains `SKILL.md` at the root.

## How to Use

1. **In OpenCode** — The skill is automatically discovered. The agent can load it via the `skill` tool when a documentation review task is detected.

2. **Manual use** (raw LLM API):
   - Load `SKILL.md` content (below the `---` frontmatter separator) as the system message.
   - Load both files from `context/` as additional context.
   - Provide the user's How-to Guide draft as the user message.
   - Set `temperature=0` for deterministic output.

3. **Expected behavior:**
   - The LLM evaluates the submitted document against all 26 criteria.
   - Output starts with a Summary section (Passed/Failed counts).
   - Failed criteria include the full criterion text and a detailed rationale.
   - Output ends with a Human Verification Warning.

## Configuration

| Setting | Value |
|---------|-------|
| Skill name | `diataxis-howto-reviewer` |
| Compatibility | `opencode` |
| Recommended model | DeepSeek v4 Pro |
| Minimum context window | 32K tokens |
| Temperature | 0.0 (deterministic) |
| Interaction mode | Single-turn (stateless) |

## Criteria Reference

| ID | Scope | Criterion |
|----|-------|-----------|
| C01 | Common | Valid heading hierarchy, no duplicates or skipped levels |
| C02 | Common | Consistent terminology and naming |
| C03 | Common | Concise, action-oriented language |
| C04 | Common | Proper formatting of commands, code blocks, placeholders |
| C05 | Common | Code blocks declare an appropriate language |
| C06 | Common | Machine-readable examples are syntactically valid |
| C07 | Common | Placeholders and example values are understandable and consistent |
| C08 | Common | Risky/destructive actions are explained beforehand |
| C09 | Common | Admonitions are not excessive and are well-placed |
| C10 | Common | Command introductions are direct, not redundant |
| H01 | How-to | Title expresses a specific practical goal |
| H02 | How-to | Title and opening paragraph align on the same goal |
| H03 | How-to | Clear statement of intent |
| H04 | How-to | Recognisable procedural structure |
| H05 | How-to | Logical sequence from start to finish |
| H06 | How-to | Steps tell the user what to DO |
| H07 | How-to | Imperative/action-oriented headings and step text |
| H08 | How-to | Avoids excessive conceptual explanation |
| H09 | How-to | Avoids reference-style content unless needed |
| H10 | How-to | Prerequisites and assumptions stated |
| H11 | How-to | Branches and alternatives clearly marked |
| H12 | How-to | Guide reaches the promised outcome |
| H13 | How-to | Verification steps with expected outputs |
| H14 | How-to | Troubleshooting/recovery instructions |
| H15 | How-to | Appropriate scope — not too broad |
| H16 | How-to | Links to further reading used sparingly |

## License

Apache-2.0
