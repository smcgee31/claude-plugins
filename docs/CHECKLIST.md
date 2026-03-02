# Plugin Checklist

Work through this when creating or updating a plugin.

## Required Structure

- [ ] `.claude-plugin/plugin.json` exists and is valid JSON
- [ ] `plugin.json` has `name` (kebab-case), `description` (<100 chars), `author.name`
- [ ] `README.md` exists with description, usage, and examples

```bash
# Validate JSON
python3 -m json.tool .claude-plugin/plugin.json
```

## Commands (`commands/`)

- [ ] Each command is a `.md` file named in kebab-case
- [ ] Includes usage, parameters, and examples

## Skills (`skills/`)

- [ ] Each skill has its own subdirectory with a `SKILL.md`
- [ ] `SKILL.md` has valid YAML frontmatter with `name` and `description`

```markdown
---
name: skill-name
description: What it does
---
```

## Agents (`agents/`)

- [ ] Each agent is a `.md` file
- [ ] Role, capabilities, and behavior guidelines are defined

## MCP (`.mcp.json`)

- [ ] Valid JSON
- [ ] All server configs are complete with `command` and `args`
- [ ] Any required env vars are documented

## Before Shipping

- [ ] All JSON files validate
- [ ] No hardcoded credentials or secrets
- [ ] Installed and tested locally in Claude Code
- [ ] All components work as described
