# Example Command

Demonstrates a basic slash command in Claude Code.

## Description

This is an example command that shows how to create custom slash commands for Claude Code plugins. When invoked, it demonstrates command execution and output.

## Usage

```
/example [options]
```

## Parameters

- `options` (optional): Additional parameters for the command

## Examples

Basic usage:
```
/example
```

With options:
```
/example --verbose
```

## Implementation Notes

This command is defined as a markdown file. The structure of this file determines how the command appears and behaves in Claude Code.

### Command Naming

The filename determines the command name. This file is `example.md`, so the command is `/example`.

### Command Documentation

The content of this markdown file serves as documentation for the command, helping users understand how to use it.

## See Also

- [Official Commands Documentation](https://code.claude.com/docs/en/plugins-reference)
- Main plugin README for more examples
