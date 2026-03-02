# Contributing to Claude Plugins

Thank you for your interest in contributing to this Claude Code plugins repository! This guide will help you create high-quality plugins that follow Anthropic's standards.

## Plugin Requirements

### Mandatory Requirements

Every plugin **must** include:

1. **`.claude-plugin/` directory** containing:
   - `plugin.json` with valid metadata (name, description, author)

2. **Valid JSON format** in all configuration files

3. **README.md** with:
   - Plugin description
   - Usage instructions
   - Any dependencies or prerequisites
   - Examples

### Recommended Components

- **Detailed documentation** of all features
- **Examples** demonstrating plugin usage
- **Clear naming conventions** (kebab-case for plugin names)
- **Version information** if applicable

## Plugin Structure Guidelines

### plugin.json Structure

```json
{
  "name": "plugin-name",
  "description": "Clear, concise description (one sentence)",
  "author": {
    "name": "Your Name",
    "email": "your.email@example.com"
  }
}
```

**Field Guidelines:**
- `name`: Use lowercase, kebab-case (e.g., "my-awesome-plugin")
- `description`: Keep under 100 characters, focus on what it does
- `author.name`: Your full name or organization
- `author.email`: Valid contact email (optional but recommended)

### Directory Organization

```
plugins/
└── your-plugin-name/
    ├── .claude-plugin/
    │   └── plugin.json
    ├── commands/           # If you have slash commands
    │   └── command.md
    ├── skills/             # If you have skills
    │   └── skill-name/
    │       └── SKILL.md
    ├── agents/             # If you have agents
    │   └── agent.md
    ├── .mcp.json           # If you integrate external tools
    └── README.md
```

## Creating Different Plugin Components

### Slash Commands (`commands/`)

Create markdown files for each command. Each file represents a command users can invoke.

**Example:** `commands/deploy.md`
```markdown
# Deploy Command

Deploys the application to production.

## Usage
/deploy [environment]

## Options
- environment: target environment (staging, production)
```

### Skills (`skills/`)

Skills are defined in `SKILL.md` files with YAML frontmatter.

**Example:** `skills/code-reviewer/SKILL.md`
```markdown
---
name: code-reviewer
description: Reviews code for best practices and potential issues
---

# Code Review Skill

This skill analyzes code and provides feedback on:
- Code quality
- Best practices
- Potential bugs
- Security issues

## Instructions

When reviewing code:
1. Check for common patterns and anti-patterns
2. Verify error handling
3. Assess code readability
4. Identify security concerns
```

### Agents (`agents/`)

Agent definitions describe specialized roles for Claude.

**Example:** `agents/test-agent.md`
```markdown
# Test Agent

A specialized agent for writing and maintaining tests.

## Capabilities
- Generate unit tests
- Create integration tests
- Suggest edge cases
- Review test coverage

## Usage
Invoke this agent when you need help with testing.
```

### MCP Configuration (`.mcp.json`)

Configure external tool integrations.

**Example:**
```json
{
  "mcpServers": {
    "server-name": {
      "command": "node",
      "args": ["path/to/server.js"],
      "env": {
        "API_KEY": "..."
      }
    }
  }
}
```

## Testing Your Plugin

Before submitting:

1. **Validate JSON files:**
   ```bash
   python3 -m json.tool .claude-plugin/plugin.json
   ```

2. **Check file structure:**
   - Verify all required files exist
   - Ensure proper directory hierarchy
   - Check that file names follow conventions

3. **Test functionality:**
   - Install the plugin locally
   - Test all commands, skills, and agents
   - Verify MCP servers connect properly

4. **Review documentation:**
   - Ensure README is complete
   - Verify examples work
   - Check for typos and clarity

## Submission Process

1. **Fork this repository**

2. **Create a new branch:**
   ```bash
   git checkout -b add-my-plugin
   ```

3. **Add your plugin:**
   - Place in `plugins/your-plugin-name/`
   - Follow all structure requirements
   - Include comprehensive README

4. **Commit your changes:**
   ```bash
   git add plugins/your-plugin-name
   git commit -m "Add [plugin-name]: brief description"
   ```

5. **Push and create a Pull Request:**
   ```bash
   git push origin add-my-plugin
   ```

6. **Fill out the PR template:**
   - Describe what your plugin does
   - List any dependencies
   - Note any special installation steps

## Code Review Criteria

Your plugin will be reviewed for:

- ✅ **Completeness:** All required files present
- ✅ **Structure:** Follows official plugin structure
- ✅ **Documentation:** Clear, comprehensive README
- ✅ **Functionality:** Works as described
- ✅ **Security:** No obvious security issues
- ✅ **Quality:** Clean code, proper formatting

## Questions?

If you have questions about contributing:

1. Check the [official Claude Code documentation](https://code.claude.com/docs/en/plugins)
2. Review existing plugins in this repository
3. Open an issue for clarification

## License

By contributing to this repository, you agree that your contributions will be licensed under the MIT License.
