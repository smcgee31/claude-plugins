# Quick Start Guide

Get started creating Claude Code plugins in minutes.

## Prerequisites

- Claude Code installed and running
- Basic understanding of markdown
- Text editor or IDE
- (Optional) Git for version control

## Create Your First Plugin

### Step 1: Choose a Template

We provide two templates:

**Minimal Plugin** - Just the essentials:
```bash
cp -r templates/minimal-plugin plugins/my-first-plugin
```

**Basic Plugin** - Includes examples of all components:
```bash
cp -r templates/basic-plugin plugins/my-first-plugin
```

### Step 2: Update Plugin Metadata

Edit `plugins/my-first-plugin/.claude-plugin/plugin.json`:

```json
{
  "name": "my-first-plugin",
  "description": "My first Claude Code plugin",
  "author": {
    "name": "Your Name",
    "email": "you@example.com"
  }
}
```

### Step 3: Add Your Content

Choose what to add to your plugin:

#### Add a Command

Create `plugins/my-first-plugin/commands/hello.md`:

```markdown
# Hello Command

Says hello to the user.

## Usage
/hello [name]

## Example
/hello World
```

#### Add a Skill

Create `plugins/my-first-plugin/skills/greeter/SKILL.md`:

```markdown
---
name: greeter
description: Friendly greeting skill
---

# Greeter Skill

This skill makes Claude extra friendly and welcoming.

## Purpose
Provides warm, welcoming greetings to users.

## Usage
Just say "greet me" or "say hello"
```

#### Add an Agent

Create `plugins/my-first-plugin/agents/helper.md`:

```markdown
# Helper Agent

A friendly assistant agent.

## Purpose
Helps users get started with the plugin.

## Capabilities
- Answers questions about the plugin
- Provides examples
- Troubleshoots issues
```

### Step 4: Document Your Plugin

Edit `plugins/my-first-plugin/README.md`:

```markdown
# My First Plugin

This is my first Claude Code plugin!

## Features
- /hello command - Says hello
- Greeter skill - Makes Claude friendly
- Helper agent - Assists with usage

## Installation
\`\`\`
/plugin install my-first-plugin@local
\`\`\`

## Usage
Try `/hello World` to get started!
```

### Step 5: Test Your Plugin

#### Validate JSON
```bash
python3 -m json.tool plugins/my-first-plugin/.claude-plugin/plugin.json
```

#### Check Structure
```bash
ls -R plugins/my-first-plugin/
```

Expected output:
```
plugins/my-first-plugin/:
.claude-plugin  commands  skills  agents  README.md

plugins/my-first-plugin/.claude-plugin:
plugin.json

plugins/my-first-plugin/commands:
hello.md

plugins/my-first-plugin/skills:
greeter

plugins/my-first-plugin/skills/greeter:
SKILL.md

plugins/my-first-plugin/agents:
helper.md
```

### Step 6: Install and Test

In Claude Code:
```
/plugin install my-first-plugin@local
```

Test your command:
```
/hello World
```

## Common Next Steps

### Add External Tool Integration

Create `.mcp.json` in your plugin root:

```json
{
  "mcpServers": {
    "my-tool": {
      "command": "node",
      "args": ["./tools/server.js"]
    }
  }
}
```

### Add Supporting Files to Skills

Skills can include helper scripts:

```
skills/
└── my-skill/
    ├── SKILL.md
    ├── helper.py
    └── config.json
```

### Add Multiple Commands

Create multiple markdown files in `commands/`:

```
commands/
├── command1.md
├── command2.md
└── command3.md
```

## Tips for Success

### Keep It Simple
Start with just one feature and expand gradually.

### Follow Conventions
- Use kebab-case for names
- Keep descriptions clear and brief
- Include examples in documentation

### Test Thoroughly
- Validate all JSON files
- Test each component independently
- Try edge cases

### Document Well
- Clear README with usage examples
- Comment complex configurations
- Provide troubleshooting tips

## Example Workflow

Here's a typical development workflow:

1. **Copy template**
   ```bash
   cp -r templates/basic-plugin plugins/my-plugin
   ```

2. **Customize metadata**
   Edit `.claude-plugin/plugin.json`

3. **Add features**
   Create commands, skills, or agents

4. **Document**
   Update README.md

5. **Validate**
   ```bash
   python3 -m json.tool .claude-plugin/plugin.json
   ```

6. **Test**
   Install and test in Claude Code

7. **Iterate**
   Refine based on testing

8. **Share**
   Commit to repository or publish

## Troubleshooting

### Plugin Won't Install

- Verify `plugin.json` is valid JSON
- Check that all required fields are present
- Ensure `.claude-plugin/` directory exists

### Command Not Working

- Verify filename matches command name
- Check markdown formatting
- Ensure file has `.md` extension

### Skill Not Activating

- Verify YAML frontmatter is valid
- Check that file is named `SKILL.md`
- Ensure skill directory is in `skills/`

## Next Steps

- Review the [Plugin Structure Reference](PLUGIN_STRUCTURE.md)
- Check out the [example plugin](../plugins/example-plugin/)
- Read [CONTRIBUTING.md](../CONTRIBUTING.md) for best practices
- Explore [official plugins](https://github.com/anthropics/claude-plugins-official)

## Getting Help

- Check the [official documentation](https://code.claude.com/docs/en/plugins)
- Review example plugins in this repository
- Search existing issues in the repository
- Open a new issue if needed

## Resources

- [Plugin Structure Reference](PLUGIN_STRUCTURE.md)
- [Example Plugin](../plugins/example-plugin/)
- [CONTRIBUTING.md](../CONTRIBUTING.md)
- [Official Documentation](https://code.claude.com/docs/en/plugins)
