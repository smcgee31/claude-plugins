# Plugin Development Checklist

Use this checklist when creating or updating Claude Code plugins to ensure completeness and quality.

## Pre-Development

- [ ] Review [PLUGIN_STRUCTURE.md](PLUGIN_STRUCTURE.md) for requirements
- [ ] Review [QUICK_START.md](QUICK_START.md) for getting started
- [ ] Review example plugin at `plugins/example-plugin/`
- [ ] Choose appropriate template (minimal or basic)

## Plugin Structure

### Required Components

- [ ] `.claude-plugin/` directory exists
- [ ] `plugin.json` exists and is valid JSON
- [ ] `plugin.json` contains `name` field
- [ ] `plugin.json` contains `description` field
- [ ] `plugin.json` contains `author` object with `name`
- [ ] Plugin name uses kebab-case
- [ ] Description is clear and under 100 characters
- [ ] README.md exists

### Optional Components

If your plugin includes commands:
- [ ] `commands/` directory exists
- [ ] Each command is a `.md` file
- [ ] Command filenames use kebab-case
- [ ] Commands have clear usage instructions

If your plugin includes skills:
- [ ] `skills/` directory exists
- [ ] Each skill has its own subdirectory
- [ ] Each skill has a `SKILL.md` file
- [ ] SKILL.md includes valid YAML frontmatter
- [ ] YAML frontmatter includes `name` and `description`

If your plugin includes agents:
- [ ] `agents/` directory exists
- [ ] Each agent is a `.md` file
- [ ] Agents have clear role definitions
- [ ] Agent capabilities are documented

If your plugin includes MCP integration:
- [ ] `.mcp.json` exists in plugin root
- [ ] `.mcp.json` is valid JSON
- [ ] MCP server configurations are complete
- [ ] External dependencies are documented

## Documentation

### README.md Requirements

- [ ] Plugin name and overview
- [ ] Clear description of what plugin does
- [ ] Installation instructions
- [ ] Usage examples for all features
- [ ] List of components (commands/skills/agents)
- [ ] Requirements and dependencies
- [ ] License information

### Additional Documentation

- [ ] Complex features are well-documented
- [ ] Examples are provided for all components
- [ ] Troubleshooting section if needed
- [ ] Configuration instructions if applicable

## Code Quality

### JSON Files

- [ ] All JSON files are valid (use `python3 -m json.tool`)
- [ ] Proper indentation (2 or 4 spaces)
- [ ] No trailing commas
- [ ] Consistent formatting

### Markdown Files

- [ ] Proper markdown formatting
- [ ] Headers used appropriately
- [ ] Code blocks have language specified
- [ ] Links are valid
- [ ] No spelling errors

### YAML Frontmatter (Skills)

- [ ] Valid YAML syntax
- [ ] Proper indentation
- [ ] Required fields present
- [ ] Frontmatter properly delimited with `---`

## Functionality

### Commands

- [ ] Command names are descriptive
- [ ] Usage instructions are clear
- [ ] Parameters are documented
- [ ] Examples are provided
- [ ] Error cases are considered

### Skills

- [ ] Skill purpose is clearly defined
- [ ] Instructions are comprehensive
- [ ] Examples demonstrate usage
- [ ] Supporting files are included if needed
- [ ] Guidelines are specific and actionable

### Agents

- [ ] Agent role is well-defined
- [ ] Capabilities are listed
- [ ] Behavior guidelines are clear
- [ ] Usage instructions are provided
- [ ] Integration with other components is documented

## Testing

### Pre-Installation Testing

- [ ] JSON validation passes for all JSON files
- [ ] Directory structure matches requirements
- [ ] All referenced files exist
- [ ] File naming follows conventions
- [ ] Documentation is complete

### Installation Testing

- [ ] Plugin installs without errors
- [ ] All components are recognized
- [ ] No conflicts with other plugins

### Functional Testing

- [ ] Commands execute correctly
- [ ] Skills activate as expected
- [ ] Agents behave appropriately
- [ ] MCP servers connect successfully (if applicable)
- [ ] Error handling works correctly

### Edge Cases

- [ ] Test with missing optional parameters
- [ ] Test with invalid inputs
- [ ] Test with edge case values
- [ ] Test concurrent usage if applicable

## Security

- [ ] No hardcoded credentials or secrets
- [ ] External dependencies are trustworthy
- [ ] User input is handled safely
- [ ] File paths are validated
- [ ] No unnecessary permissions required

## Performance

- [ ] Plugin loads quickly
- [ ] Commands execute efficiently
- [ ] No unnecessary resource usage
- [ ] Large files handled appropriately

## Version Control

- [ ] `.gitignore` excludes build artifacts
- [ ] Commit messages are clear
- [ ] Changes are logically grouped
- [ ] Version number updated (if versioning)
- [ ] CHANGELOG updated (if maintained)

## Release

- [ ] All tests pass
- [ ] Documentation is up to date
- [ ] Version bumped appropriately
- [ ] Release notes prepared
- [ ] Dependencies documented
- [ ] License specified
- [ ] Author information correct

## Post-Release

- [ ] Installation instructions verified
- [ ] Plugin works in clean environment
- [ ] Documentation accessible
- [ ] Support channels established
- [ ] Feedback mechanism in place

## Maintenance

- [ ] Issues are tracked
- [ ] Bug fixes are prioritized
- [ ] Feature requests are evaluated
- [ ] Dependencies are updated
- [ ] Security updates applied promptly

## Checklist for Reviewers

If reviewing someone else's plugin:

- [ ] Structure follows requirements
- [ ] JSON files are valid
- [ ] Documentation is complete
- [ ] Code quality is acceptable
- [ ] Security concerns addressed
- [ ] Testing appears adequate
- [ ] No obvious bugs or issues
- [ ] Naming conventions followed
- [ ] Examples are helpful
- [ ] Plugin serves clear purpose

## Quick Validation Commands

```bash
# Validate plugin.json
python3 -m json.tool .claude-plugin/plugin.json

# Validate .mcp.json (if exists)
python3 -m json.tool .mcp.json

# Check required structure
test -d .claude-plugin && echo "✓ .claude-plugin exists" || echo "✗ Missing"
test -f .claude-plugin/plugin.json && echo "✓ plugin.json exists" || echo "✗ Missing"
test -f README.md && echo "✓ README.md exists" || echo "✗ Missing"

# List all files
find . -type f -not -path "./.git/*"
```

## Resources

- [PLUGIN_STRUCTURE.md](PLUGIN_STRUCTURE.md) - Detailed structure reference
- [QUICK_START.md](QUICK_START.md) - Getting started guide
- [CONTRIBUTING.md](../CONTRIBUTING.md) - Contribution guidelines
- [Example Plugin](../plugins/example-plugin/) - Reference implementation
- [Official Documentation](https://code.claude.com/docs/en/plugins)
