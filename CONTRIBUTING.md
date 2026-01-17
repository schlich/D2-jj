# Contributing to D2-jj

Thank you for your interest in contributing to D2-jj! This document provides guidelines for contributing to the framework.

## Ways to Contribute

- **Add new examples**: Show different graph patterns or scenarios
- **Improve documentation**: Clarify explanations, fix typos, add details
- **Create new themes**: Alternative style schemes for different needs
- **Share use cases**: Document how you're using the framework
- **Report issues**: Identify problems or unclear aspects
- **Suggest improvements**: Propose new conventions or features

## Getting Started

1. Fork the repository
2. Clone your fork locally
3. Create a feature branch
4. Make your changes
5. Test your changes
6. Submit a pull request

## Contribution Guidelines

### Code of Conduct

- Be respectful and constructive
- Focus on what is best for the community
- Show empathy towards other community members

### D2 Examples

When adding new examples:

1. **Follow conventions**: Use the patterns defined in CONVENTIONS.md
2. **Import theme**: Always import `styles/default-theme.d2`
3. **Add comments**: Explain what the example demonstrates
4. **Test rendering**: Verify the example renders correctly
5. **Use clear labels**: Keep commit messages concise but descriptive
6. **Include notes**: Add explanatory text where helpful

Example template:
```d2
# Example Name
# Brief description of what this demonstrates
# Render with: d2 example-name.d2 example-name.svg

...@../styles/default-theme.d2

direction: up

# Your diagram code here
```

### Documentation

When improving documentation:

1. **Be clear and concise**: Use simple language
2. **Provide examples**: Show, don't just tell
3. **Check spelling**: Proofread your changes
4. **Maintain consistency**: Match the existing style and tone
5. **Update related files**: Keep all docs in sync

### Themes and Styles

When creating new themes:

1. **Base on default**: Start from `styles/default-theme.d2`
2. **Document colors**: Explain color choices
3. **Maintain classes**: Keep the same class names
4. **Test with examples**: Verify with all examples
5. **Provide rationale**: Explain the theme's purpose

### Naming Conventions

- **Files**: Use kebab-case (e.g., `merge-scenario.d2`)
- **Directories**: Use lowercase (e.g., `examples/`, `styles/`)
- **Classes**: Use kebab-case (e.g., `commit-immutable`)
- **Identifiers**: Use snake_case in D2 code (e.g., `merge_commit`)

## Testing Your Changes

Before submitting:

1. **Render examples**: Ensure all examples still render correctly
   ```bash
   d2 examples/your-example.d2 test-output.svg
   ```

2. **Check syntax**: Verify D2 syntax is correct
   ```bash
   d2 --version  # Ensure D2 is installed
   ```

3. **Review output**: Visually inspect rendered diagrams

4. **Test references**: Verify internal links in markdown files

5. **Check formatting**: Ensure consistent formatting

## Commit Messages

Use clear, descriptive commit messages:

- **Format**: `<type>: <description>`
- **Types**: 
  - `feat`: New feature or example
  - `fix`: Bug fix or correction
  - `docs`: Documentation changes
  - `style`: Formatting, styling changes
  - `refactor`: Code restructuring
  - `test`: Adding or updating tests
  - `chore`: Maintenance tasks

Examples:
```
feat: add parallel-branches example
docs: clarify rebase scenario explanation
style: update color scheme for better contrast
fix: correct edge direction in merge example
```

## Pull Request Process

1. **Create descriptive PR**: Explain what and why
2. **Reference issues**: Link to related issues if applicable
3. **Include examples**: Show rendered output if relevant
4. **Update docs**: Modify documentation as needed
5. **Be responsive**: Address review comments promptly

### PR Template

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] New example
- [ ] Documentation update
- [ ] New theme/style
- [ ] Bug fix
- [ ] Other (specify)

## Testing
- [ ] Rendered successfully with D2
- [ ] Visually inspected output
- [ ] Follows framework conventions
- [ ] Documentation updated

## Screenshots (if applicable)
[Attach rendered diagram images]

## Related Issues
Closes #issue_number
```

## Style Guidelines

### D2 Code Style

```d2
# Good: Clear structure, consistent indentation
commit_id: {
  label: "abc1234\nCommit message"
  class: commit
  style.fill: "#FFFFFF"
}

# Good: Descriptive identifiers
merge_commit -> feature_branch
merge_commit -> main_branch

# Avoid: Vague identifiers
c1 -> c2
```

### Markdown Style

- Use headings hierarchically (don't skip levels)
- Use code blocks with language tags
- Use lists for multiple items
- Keep lines reasonably short (80-100 chars)
- Use bold for **emphasis**, italics for *references*

### Comments

```d2
# Good: Explains purpose or context
# This represents the conflict state before resolution
conflict_commit: {
  label: "abc1234\n⚠ CONFLICT"
  class: commit-conflict
}

# Avoid: States the obvious
# This is a commit
commit: { }
```

## Project Structure

When adding files, maintain the structure:

```
D2-jj/
├── README.md                # Main entry point
├── CONVENTIONS.md           # Framework conventions
├── GETTING_STARTED.md       # Tutorial for new users
├── CONTRIBUTING.md          # This file
├── examples/                # Example diagrams
│   └── new-example.d2       # Add new examples here
├── styles/                  # Style themes
│   └── new-theme.d2         # Add new themes here
├── templates/               # Starter templates
└── docs/                    # Additional documentation (if needed)
```

## Review Criteria

Pull requests are evaluated on:

1. **Correctness**: Does it work as intended?
2. **Clarity**: Is it easy to understand?
3. **Consistency**: Does it follow conventions?
4. **Completeness**: Is documentation included?
5. **Value**: Does it add meaningful functionality?

## Questions or Need Help?

- Open an issue for discussion
- Ask questions in pull request comments
- Review existing examples and documentation
- Check the [D2 documentation](https://d2lang.com/)

## Recognition

Contributors will be:
- Listed in project documentation
- Mentioned in release notes
- Appreciated by the community

Thank you for contributing to D2-jj! 🙏
