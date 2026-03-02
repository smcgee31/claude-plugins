# Plugin Structure Reference

This document provides a comprehensive reference for Claude Code plugin structure and requirements.

## Directory Structure

### Required Structure

```
plugin-name/
└── .claude-plugin/
    └── plugin.json       # REQUIRED
```

### Complete Structure

```
plugin-name/
├── .claude-plugin/
│   └── plugin.json          # Plugin metadata (REQUIRED)
├── .mcp.json                # MCP server configuration (optional)
├── commands/                # Slash commands (optional)
│   ├── command1.md
│   └── command2.md
├── skills/                  # Skills (optional)
│   ├── skill1/
│   │   └── SKILL.md
│   └── skill2/
│       ├── SKILL.md
│       └── helper.py        # Supporting files
├── agents/                  # Agents (optional)
│   ├── agent1.md
│   └── agent2.md
├── hooks/                   # Event hooks (optional)
│   └── hooks.json
└── README.md                # Documentation (recommended)
```

## plugin.json Reference

### Required Fields

```json
{
  "name": "string",
  "description": "string",
  "author": {
    "name": "string"
  }
}
```

### Complete Schema

```json
{
  "name": "string",              // REQUIRED: Unique plugin identifier
  "description": "string",       // REQUIRED: Brief description
  "author": {                    // REQUIRED: Author information
    "name": "string",            // REQUIRED: Author name
    "email": "string",           // Optional: Contact email
    "url": "string"              // Optional: Author website
  },
  "version": "string",           // Optional: Semantic version
  "homepage": "string",          // Optional: Plugin homepage
  "repository": {                // Optional: Source repository
    "type": "git",
    "url": "string"
  },
  "license": "string",           // Optional: License identifier
  "keywords": ["string"],        // Optional: Search keywords
  "engines": {                   // Optional: Version requirements
    "claude": ">=1.0.0"
  }
}
```

### Field Specifications

#### name
- **Type:** string
- **Required:** Yes
- **Format:** kebab-case recommended
- **Example:** `"my-awesome-plugin"`
- **Notes:** Must be unique within the plugin registry

#### description
- **Type:** string
- **Required:** Yes
- **Length:** Recommended < 100 characters
- **Example:** `"Provides code review capabilities and suggestions"`
- **Notes:** Used in plugin discovery and listings

#### author
- **Type:** object
- **Required:** Yes
- **Fields:**
  - `name` (required): Author or organization name
  - `email` (optional): Contact email
  - `url` (optional): Website or profile URL

#### version
- **Type:** string
- **Required:** No
- **Format:** Semantic versioning (e.g., "1.0.0")
- **Example:** `"1.2.3"`

## Commands

### File Format
- **Location:** `commands/` directory
- **Format:** Markdown (.md)
- **Naming:** Filename becomes command name (e.g., `deploy.md` → `/deploy`)

### Structure
```markdown
# Command Title

Description of what the command does.

## Usage
/command-name [parameters]

## Parameters
- param1: Description
- param2: Description

## Examples
/command-name example-value
```

## Skills

### File Format
- **Location:** `skills/{skill-name}/` directory
- **Format:** Markdown with YAML frontmatter
- **Filename:** Must be `SKILL.md`

### Structure
```markdown
---
name: skill-name
description: Brief description
version: 1.0.0          # Optional
tags: [tag1, tag2]      # Optional
---

# Skill Title

Detailed description and instructions...
```

### Supporting Files
Skills can include additional files in their directory:
- Python scripts (`.py`)
- JavaScript files (`.js`)
- Data files (`.json`, `.yaml`)
- Documentation (`.md`)

## Agents

### File Format
- **Location:** `agents/` directory
- **Format:** Markdown (.md)
- **Naming:** Descriptive filename (e.g., `test-agent.md`)

### Structure
```markdown
# Agent Name

Description of the agent's role and purpose.

## Capabilities
- Capability 1
- Capability 2

## Behavior Guidelines
1. Guideline 1
2. Guideline 2

## Usage
How to invoke the agent...
```

## MCP Configuration

### File Format
- **Location:** Root directory
- **Filename:** `.mcp.json`
- **Format:** JSON

### Structure
```json
{
  "mcpServers": {
    "server-name": {
      "command": "string",       // Executable command
      "args": ["string"],        // Command arguments
      "env": {                   // Environment variables
        "KEY": "value"
      }
    }
  }
}
```

### Example
```json
{
  "mcpServers": {
    "my-tool": {
      "command": "node",
      "args": ["./server.js"],
      "env": {
        "API_KEY": "${API_KEY}",
        "DEBUG": "false"
      }
    }
  }
}
```

## Hooks

### File Format
- **Location:** `hooks/` directory or inline in `plugin.json`
- **Format:** JSON

### Structure
```json
{
  "hooks": {
    "onInstall": "script to run on install",
    "onUpdate": "script to run on update",
    "onUninstall": "script to run on uninstall"
  }
}
```

## Best Practices

### Naming Conventions
- **Plugin names:** kebab-case (e.g., `my-plugin`)
- **Command files:** kebab-case (e.g., `deploy-prod.md`)
- **Skill directories:** kebab-case (e.g., `code-reviewer/`)
- **Agent files:** kebab-case (e.g., `test-agent.md`)

### File Organization
- Keep related files together
- Use subdirectories for complex components
- Include README files for documentation
- Maintain flat structure when possible

### Documentation
- Every plugin needs a README.md
- Document all parameters and options
- Provide usage examples
- Include troubleshooting tips

### Version Control
- Use semantic versioning
- Tag releases in git
- Maintain CHANGELOG.md
- Document breaking changes

## Validation

### JSON Validation
```bash
# Validate plugin.json
python3 -m json.tool .claude-plugin/plugin.json

# Validate .mcp.json
python3 -m json.tool .mcp.json
```

### Structure Validation
Ensure:
- [ ] `.claude-plugin/` directory exists
- [ ] `plugin.json` is valid JSON
- [ ] Required fields present
- [ ] Directory structure follows conventions
- [ ] All referenced files exist

## Common Patterns

### Simple Command Plugin
```
my-command-plugin/
├── .claude-plugin/
│   └── plugin.json
├── commands/
│   └── mycommand.md
└── README.md
```

### Skill Plugin
```
my-skill-plugin/
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   └── my-skill/
│       ├── SKILL.md
│       └── helper.py
└── README.md
```

### Full-Featured Plugin
```
comprehensive-plugin/
├── .claude-plugin/
│   └── plugin.json
├── .mcp.json
├── commands/
│   ├── cmd1.md
│   └── cmd2.md
├── skills/
│   ├── skill1/
│   │   └── SKILL.md
│   └── skill2/
│       └── SKILL.md
├── agents/
│   ├── agent1.md
│   └── agent2.md
└── README.md
```

## Resources

- [Official Plugin Documentation](https://code.claude.com/docs/en/plugins)
- [Anthropic Official Plugins](https://github.com/anthropics/claude-plugins-official)
- Repository CONTRIBUTING.md
- Repository README.md
