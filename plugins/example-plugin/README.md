# Example Plugin

A comprehensive example demonstrating all Claude Code plugin capabilities including commands, agents, skills, and MCP server integration.

## Overview

This plugin serves as a reference implementation showing how to:
- Define slash commands
- Create custom skills
- Configure agents
- Integrate external tools via MCP

## Installation

To install this plugin in Claude Code:

```
/plugin install example-plugin@your-registry
```

## Components

### Commands

- `/example` - Demonstrates a basic slash command

### Skills

- **code-reviewer** - Analyzes code for quality and best practices

### Agents

- **example-agent** - A specialized agent demonstrating agent configuration

## Usage

### Using Commands

```
/example
```

This will execute the example command and demonstrate command output.

### Using Skills

Skills are automatically available when the plugin is installed. The code-reviewer skill activates when you ask Claude to review code.

### Using Agents

Agents can be invoked through natural language or specific commands defined in their configuration.

## Development

This plugin demonstrates the complete structure for Claude Code plugins:

```
example-plugin/
├── .claude-plugin/
│   └── plugin.json          # Plugin metadata
├── commands/
│   └── example.md           # Example command
├── skills/
│   └── code-reviewer/
│       └── SKILL.md         # Example skill
├── agents/
│   └── example-agent.md     # Example agent
└── README.md                # This file
```

## Requirements

- Claude Code (latest version)
- No external dependencies

## License

MIT License - See repository LICENSE file for details.

## Contributing

This is an example plugin. For creating your own plugins, see the main repository README and CONTRIBUTING.md.
