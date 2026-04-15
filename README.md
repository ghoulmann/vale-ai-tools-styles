# Vale AI Tools Style Guide

> **Note:** The `.ini` configuration files in this repository are not ready to use out of the box. They will need to be reviewed and adjusted to match your specific environment, file paths, and style preferences before use.

A comprehensive Vale style guide for AI-assisted development tools, ensuring consistent and professional documentation across Claude Code, Windsurf, and GitHub Copilot.

## Overview

This repository contains Vale linting rules specifically tailored for documentation related to AI coding assistants. It enforces proper terminology, spelling, formatting, and branding guidelines for:

- **Claude Code**: Anthropic's AI-powered coding environment
- **Windsurf**: Codeium's AI-enhanced IDE
- **GitHub Copilot**: GitHub's AI pair programmer

## Features

- **Terminology Enforcement**: Correct capitalization and naming of product terms
- **Spelling Corrections**: Automatic fixes for common misspellings
- **Formatting Rules**: Enforces backticks around filenames, commands, and code elements
- **Plan and Feature Names**: Proper capitalization of subscription plans and features
- **UI Element Consistency**: Standardized phrasing for interface elements
- **Competitor References**: Correct naming of competing products

## Installation

### Prerequisites

- [Vale](https://vale.sh/) (version 2.0 or later)
- Git

### Setup

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/vale-ai-tools.git
   cd vale-ai-tools
   ```

2. Copy the styles to your Vale configuration:
   ```bash
   # Option 1: Copy to global Vale styles
   cp -r styles/* ~/.vale/styles/

   # Option 2: Use as a local style directory
   # Add to your .vale.ini:
   # StylesPath = /path/to/vale-ai-tools/styles
   ```

3. Configure your `.vale.ini` file:
   ```ini
   StylesPath = styles
   MinAlertLevel = warning

   [*.md]
   BasedOnStyles = Vale, proselint, Custom, ClaudeCode, Windsurf, GitHubCopilot

   [*.mdx]
   BasedOnStyles = Vale, proselint, Custom, ClaudeCode, Windsurf, GitHubCopilot
   ```

## Usage

### Basic Linting

Run Vale on your Markdown files:

```bash
vale your-documentation.md
```

### With Specific Styles

To use only certain AI tool styles:

```ini
[*.md]
BasedOnStyles = Vale, ClaudeCode, GitHubCopilot
```

### CI/CD Integration

Add to your GitHub Actions workflow:

```yaml
- name: Lint documentation
  uses: errata-ai/vale-action@v2
  with:
    files: docs/
    config: .vale.ini
  env:
    GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

## Style Guide Structure

```
styles/
├── ClaudeCode/          # Rules for Claude Code documentation
│   ├── Acronyms.yml     # AI, CLI, etc.
│   ├── BuiltInTools.yml # Tool naming
│   ├── ConfigPaths.yml  # Configuration file paths
│   ├── FeatureNames.yml # Feature terminology
│   ├── HookEvents.yml   # Event naming
│   ├── MisStylings.yml  # Common misspellings and formatting
│   ├── PermissionModes.yml # Permission terminology
│   ├── SlashCommands.yml # /command formatting
│   ├── Spelling.yml     # Spelling corrections
│   ├── SubagentTypes.yml # Subagent naming
│   └── Terminology.yml  # Core terminology
├── Common/              # General writing rules
│   ├── AvoidJargon.yml
│   ├── HeadingStyle.yml
│   ├── ImperativeVoice.yml
│   ├── KeyboardShortcuts.yml
│   ├── LinkText.yml
│   ├── OxfordComma.yml
│   ├── PassiveVoice.yml
│   ├── SecondPerson.yml
│   └── Tone.yml
├── Custom/              # Custom rules
│   └── MaxLength.yml    # Sentence/paragraph length limits
├── GitHubCopilot/       # Rules for GitHub Copilot documentation
│   ├── Acronyms.yml
│   ├── CompetitorNames.yml
│   ├── MisStylings.yml
│   ├── PlanNames.yml
│   ├── Spelling.yml
│   ├── Terminology.yml
│   └── UIElements.yml
└── Windsurf/            # Rules for Windsurf documentation
    ├── Acronyms.yml
    ├── CompetitorNames.yml
    ├── MisStylings.yml
    ├── PlanNames.yml
    ├── Spelling.yml
    ├── Terminology.yml
    └── UIElements.yml
```

## Key Rules

### Formatting Requirements

- **Filenames and Paths**: Must be wrapped in backticks (e.g., `CLAUDE.md`, `.codeiumignore`)
- **Commands**: Terminal and slash commands must be in backticks (e.g., `/compact`, `gh repo`)
- **Code Elements**: Inline code should use backticks

### Terminology Examples

| Incorrect | Correct |
|-----------|---------|
| claude code | Claude Code |
| windsurf | Windsurf |
| github copilot | GitHub Copilot |
| cascade | Cascade |
| copilot pro | Copilot Pro |
| agent teams | agent teams |

### Plan Names

- Claude Code: Standard plans
- Windsurf: Free plan, Pro plan, Max plan, Teams plan, Enterprise plan
- GitHub Copilot: Copilot Free, Copilot Pro, Copilot Pro+, Copilot Business, Copilot Enterprise

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b add-new-rule`
3. Add or modify rules in the appropriate style directory
4. Test your changes: `vale test-file.md`
5. Commit and push: `git commit -m "Add new rule for X"`
6. Create a Pull Request

### Adding New Rules

- Follow the existing YAML structure
- Use `extends: substitution` for most rules
- Set appropriate `level` (error, warning, suggestion)
- Include `ignorecase: true` for case-insensitive matching
- Test rules thoroughly

### Rule Categories

- **Terminology.yml**: Product names, feature names, proper nouns
- **MisStylings.yml**: Common typos, hyphenation issues, formatting
- **Spelling.yml**: General spelling corrections
- **Acronyms.yml**: AI, CLI, API, etc.
- **PlanNames.yml**: Subscription plan naming
- **UIElements.yml**: Interface element references

## Testing

Test your rules with sample content:

```bash
# Test all rules
vale --config .vale.ini test-file.md

# Test specific style
vale --config .vale.ini --style GitHubCopilot test-file.md
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Related Projects

- [Vale](https://vale.sh/) - The command-line tool
- [Vale Styles](https://github.com/errata-ai/styles) - Official Vale style collections
- [Claude Code](https://docs.anthropic.com/claude/docs/claude-code) - Claude Code documentation
- [Windsurf](https://docs.windsurf.com/) - Windsurf documentation
- [GitHub Copilot](https://docs.github.com/en/copilot) - GitHub Copilot documentation

## Support

- [Vale Documentation](https://vale.sh/docs/)
- [GitHub Issues](https://github.com/yourusername/vale-ai-tools/issues)
- [Vale Community](https://github.com/errata-ai/vale/discussions)

---

*Maintained with ❤️ for consistent AI tool documentation*