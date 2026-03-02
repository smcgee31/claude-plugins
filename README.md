# Claude Plugins

My personal Claude Code plugins.

## Plugins

| Plugin | Description |
|--------|-------------|
| [example-plugin](plugins/example-plugin/) | Reference implementation (commands, skills, agents) |

## Adding a New Plugin

1. Copy the example: `cp -r plugins/example-plugin plugins/my-plugin`
2. Update `plugins/my-plugin/.claude-plugin/plugin.json`
3. Replace the commands/skills/agents with your own
4. Work through `docs/CHECKLIST.md`

## Plugin Structure

```
plugin-name/
├── .claude-plugin/
│   └── plugin.json      # required: name, description, author
├── commands/            # slash commands — one .md file per command
├── skills/              # each skill gets a subdirectory with SKILL.md
├── agents/              # agent definitions as .md files
├── .mcp.json            # optional MCP server config
└── README.md
```

### plugin.json

```json
{
  "name": "plugin-name",
  "description": "What it does",
  "author": { "name": "Your Name" }
}
```
