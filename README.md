# Claude Code Plugins Repository

A repository for Claude Code plugins following Anthropic's official plugin structure and requirements.

## What are Claude Code Plugins?

Claude Code plugins extend the capabilities of Claude Code by adding custom commands, skills, agents, and tool integrations. Plugins follow a standardized structure that makes them easy to install, discover, and share.

## Repository Structure

```
claude-plugins/
├── .claude-plugin/           # Repository-level plugin metadata (optional)
├── plugins/                  # Your plugins go here
│   └── example-plugin/       # Example plugin structure
├── templates/                # Plugin templates for quick start
├── docs/                     # Additional documentation
├── README.md                 # This file
├── CONTRIBUTING.md           # Plugin development guidelines
└── LICENSE                   # MIT License
```

## Plugin Structure

Each plugin must follow this structure:

```
plugin-name/
├── .claude-plugin/
│   └── plugin.json          # REQUIRED: Plugin metadata
├── .mcp.json                # Optional: MCP server configuration
├── commands/                # Optional: Slash commands
├── agents/                  # Optional: Agent definitions
├── skills/                  # Optional: Skill definitions
└── README.md                # Recommended: Plugin documentation
```

### Required Files

#### `.claude-plugin/plugin.json`

Every plugin **must** include a `plugin.json` file with the following structure:

```json
{
  "name": "your-plugin-name",
  "description": "A brief description of your plugin",
  "author": {
    "name": "Your Name",
    "email": "your.email@example.com"
  }
}
```

**Required Fields:**
- `name`: Unique identifier for your plugin (kebab-case recommended)
- `description`: Human-readable description for plugin discovery
- `author`: Object containing at least the `name` field

### Optional Components

#### Commands (`commands/`)
Individual markdown files representing slash commands that users can invoke in Claude Code.

#### Skills (`skills/`)
Directories containing `SKILL.md` files with YAML frontmatter and task instructions. Skills can include supporting scripts and assets.

#### Agents (`agents/`)
Markdown files detailing specialized agent roles and capabilities.

#### MCP Configuration (`.mcp.json`)
JSON configuration for Model Context Protocol servers to integrate external tools.

## Getting Started

### Creating a New Plugin

1. **Use the template:**
   ```bash
   cp -r templates/basic-plugin plugins/my-new-plugin
   ```

2. **Update plugin.json:**
   Edit `plugins/my-new-plugin/.claude-plugin/plugin.json` with your plugin details.

3. **Add your content:**
   - Add commands to `commands/`
   - Add skills to `skills/`
   - Add agents to `agents/`
   - Configure MCP servers in `.mcp.json`

4. **Document your plugin:**
   Update the `README.md` in your plugin directory.

### Installing Plugins

To install a plugin from this repository in Claude Code:

```
/plugin install {plugin-name}@{registry}
```

Or browse for plugins in `/plugin > Discover`

## Best Practices

- **Use meaningful names:** Choose descriptive, kebab-case names for plugins
- **Document thoroughly:** Include comprehensive README files
- **Version control:** Track changes to your plugins with clear commit messages
- **Test thoroughly:** Ensure all commands, skills, and agents work as expected
- **Security first:** Only include trusted tools and scripts

## Resources

- [Official Claude Code Plugin Documentation](https://code.claude.com/docs/en/plugins)
- [Anthropic Official Plugins Repository](https://github.com/anthropics/claude-plugins-official)
- [Complete Guide to Building Skills for Claude](https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf)

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on contributing plugins to this repository.

## License

This repository is licensed under the MIT License. See [LICENSE](LICENSE) for details.

Individual plugins may have their own licenses - please check each plugin's directory for details.
