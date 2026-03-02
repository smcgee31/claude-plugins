---
name: code-reviewer
description: Analyzes code for quality, best practices, and potential issues
---

# Code Review Skill

This skill provides comprehensive code review capabilities, analyzing code for quality, maintainability, security, and adherence to best practices.

## Purpose

When activated, this skill helps Claude:
- Review code for common issues and anti-patterns
- Suggest improvements and optimizations
- Identify potential bugs and edge cases
- Check for security vulnerabilities
- Assess code readability and maintainability

## Review Criteria

### Code Quality
- Clean, readable code structure
- Appropriate use of language features
- Proper error handling
- Efficient algorithms and data structures

### Best Practices
- Following language-specific conventions
- Proper naming conventions
- Appropriate use of comments
- Code modularity and reusability

### Security
- Input validation
- Secure data handling
- Authentication and authorization
- Protection against common vulnerabilities (SQL injection, XSS, etc.)

### Maintainability
- Clear code organization
- Appropriate abstraction levels
- Documentation quality
- Test coverage

## Usage

This skill is automatically available when the plugin is installed. To use it:

```
Review this code for any issues:
[paste your code here]
```

Or more specifically:

```
Check this function for security vulnerabilities:
[paste your code here]
```

## Example Reviews

### Example 1: Security Review

**Input:**
```python
def login(username, password):
    query = f"SELECT * FROM users WHERE username='{username}' AND password='{password}'"
    return db.execute(query)
```

**Review Output:**
- ⚠️ SQL Injection vulnerability: User input is directly interpolated into SQL query
- ⚠️ Passwords should be hashed, not stored in plain text
- Recommendation: Use parameterized queries and proper password hashing

### Example 2: Code Quality Review

**Input:**
```javascript
function calc(a,b,c){return c=='add'?a+b:c=='sub'?a-b:c=='mul'?a*b:a/b}
```

**Review Output:**
- ❌ Poor readability: Single-line nested ternary operators
- ❌ Missing error handling for division by zero
- ❌ No input validation
- Recommendation: Refactor into clear conditional statements with proper error handling

## Supporting Files

This skill directory can include:
- Additional documentation
- Example code samples
- Supporting scripts or utilities
- Test cases

## Configuration

No additional configuration is required. The skill is available immediately upon plugin installation.
