# D2-jj

A framework and set of conventions for visualizing JJ (Jujutsu) changeset and commit graphs using D2 diagrams.

## Overview

D2-jj provides standardized patterns, styles, and examples for creating clear and consistent visualizations of version control graphs from JJ repositories. Whether you're documenting workflows, explaining merge strategies, or illustrating repository structure, D2-jj offers a systematic approach to representing JJ concepts visually.

## Features

- **Standardized conventions** for representing commits, branches, and relationships
- **Reusable style themes** for consistent visual appearance
- **Example templates** for common graph patterns
- **Best practices** for clear and effective diagrams
- **Complete documentation** of framework conventions

## Quick Start

### 1. Install D2

First, install the D2 diagram tool:

```bash
# macOS
brew install d2

# Linux
curl -fsSL https://d2lang.com/install.sh | sh -s --

# Windows
scoop install d2
```

See [D2 installation docs](https://d2lang.com/#install) for more options.

### 2. Use the Framework

Choose an example or template to get started:

```bash
# Render a linear history example
d2 examples/linear-history.d2 output.svg

# Render a branching example
d2 examples/branching.d2 output.svg

# Render a complex graph
d2 examples/complex-graph.d2 output.svg
```

### 3. Create Your Own Diagrams

Start with a template or example, then customize:

```d2
# Import the default theme
...@styles/default-theme.d2

direction: up

# Define your commits
my_commit: {
  label: "abcd1234\nMy changes"
  class: commit
}

# Add relationships, branches, etc.
```

## Framework Structure

```
D2-jj/
├── CONVENTIONS.md           # Detailed framework conventions
├── README.md                # This file
├── examples/                # Example diagrams
│   ├── linear-history.d2    # Simple linear commit history
│   ├── branching.d2         # Multiple branches
│   ├── merge-commits.d2     # Merge commit examples
│   └── complex-graph.d2     # Complex realistic scenario
├── styles/                  # Reusable style definitions
│   └── default-theme.d2     # Default theme and classes
└── templates/               # Starting templates
    ├── basic-commit.d2      # Single commit template
    └── branch-pointer.d2    # Branch reference template
```

## Key Conventions

### Commits

Represented as rectangles with rounded corners:

```d2
commit_id: {
  label: "change_id\nCommit message"
  class: commit
}
```

### Branch Pointers

Represented as hexagons with color coding:

```d2
main: {
  label: "main"
  class: branch-main  # Green hexagon
}
main -> commit_id
```

### Relationships

Directed edges from child to parent:

```d2
child_commit -> parent_commit
```

### Working Copy

Represented as an orange circle with @ symbol:

```d2
wc: {
  label: "@"
  class: working-copy
}
wc -> current_commit
```

## Color Scheme

| Element | Color | Purpose |
|---------|-------|---------|
| Main branch | Green (#4CAF50) | Primary development branch |
| Feature branch | Blue (#2196F3) | Feature/topic branches |
| Working copy | Orange (#FF9800) | Current working location |
| Bookmark/Tag | Purple (#9C27B0) | Named references |
| Immutable commit | Gray (#E0E0E0) | Pushed/immutable commits |
| Conflict | Red border (#F44336) | Conflicted states |

## Examples

### Linear History

```d2
direction: up
commit2 -> commit1
commit1 -> commit0
```

Creates a simple vertical chain showing the evolution of commits.

### Branching

```d2
direction: up
feature_commit -> base_commit
main_commit -> base_commit
```

Shows two branches diverging from a common ancestor.

### Merge Commit

```d2
direction: up
merge_commit -> feature_commit
merge_commit -> main_commit
```

Illustrates a merge commit with two parent relationships.

## Documentation

For detailed information about conventions, patterns, and best practices, see:

- [CONVENTIONS.md](CONVENTIONS.md) - Complete framework conventions and guidelines

## Use Cases

- **Documentation**: Illustrate repository structure in docs
- **Tutorials**: Explain JJ workflows and concepts
- **Planning**: Visualize branching strategies
- **Communication**: Share repository state with team
- **Education**: Teach version control concepts

## Rendering Options

D2 supports multiple output formats:

```bash
# SVG (vector graphics)
d2 input.d2 output.svg

# PNG (raster graphics)
d2 input.d2 output.png

# PDF
d2 input.d2 output.pdf

# Apply specific theme
d2 --theme=0 input.d2 output.svg
```

## Advanced Features

### Custom Styling

Override default styles for specific needs:

```d2
commit_special: {
  label: "Special commit"
  shape: rectangle
  style.border-radius: 5
  style.fill: "#FFD700"
  style.font-color: "#000000"
}
```

### Containers

Group related commits:

```d2
feature_work: {
  commit1: { label: "Change 1" }
  commit2: { label: "Change 2" }
  commit2 -> commit1
}
```

### Annotations

Add explanatory notes:

```d2
note: "This merge resolved conflicts" {
  shape: text
  style.italic: true
}
```

## Contributing

To contribute improvements:

1. Follow existing conventions in CONVENTIONS.md
2. Test examples render correctly with D2
3. Update documentation as needed
4. Maintain consistency with established patterns

## Resources

- [D2 Documentation](https://d2lang.com/)
- [D2 Playground](https://play.d2lang.com/) - Test diagrams online
- [Jujutsu Documentation](https://github.com/martinvonz/jj)
- [JJ Tutorial](https://steveklabnik.github.io/jujutsu-tutorial/)

## License

This framework is provided as-is for community use.