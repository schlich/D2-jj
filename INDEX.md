# D2-jj Documentation Index

Complete guide to all documentation in the D2-jj framework.

## Quick Links

| Document | Purpose | For |
|----------|---------|-----|
| [README.md](README.md) | Overview and quick start | Everyone |
| [GETTING_STARTED.md](GETTING_STARTED.md) | Step-by-step tutorial | New users |
| [QUICK_REFERENCE.md](QUICK_REFERENCE.md) | Quick lookup | Regular users |
| [CONVENTIONS.md](CONVENTIONS.md) | Complete conventions | Detailed reference |
| [USAGE_EXAMPLES.md](USAGE_EXAMPLES.md) | Real-world scenarios | Practical use |
| [TESTING.md](TESTING.md) | Testing guide | Contributors |
| [CONTRIBUTING.md](CONTRIBUTING.md) | Contribution guide | Contributors |
| [CHANGELOG.md](CHANGELOG.md) | Version history | Everyone |

## Documentation Map

### For First-Time Users

1. **Start here**: [README.md](README.md)
   - What D2-jj is and why use it
   - Quick overview of features
   - Installation instructions

2. **Then read**: [GETTING_STARTED.md](GETTING_STARTED.md)
   - Step-by-step tutorial
   - Create your first diagram
   - Common workflows

3. **Explore**: [Examples](examples/)
   - See working examples
   - Render and view them
   - Use as templates

### For Regular Users

1. **Quick lookup**: [QUICK_REFERENCE.md](QUICK_REFERENCE.md)
   - Common patterns
   - Class reference
   - Color codes
   - Rendering commands

2. **Practical guide**: [USAGE_EXAMPLES.md](USAGE_EXAMPLES.md)
   - Real-world scenarios
   - Feature branch workflows
   - Rebase operations
   - Conflict resolution
   - Release branches

3. **Deep dive**: [CONVENTIONS.md](CONVENTIONS.md)
   - Complete conventions
   - Best practices
   - Advanced patterns
   - Style guidelines

### For Contributors

1. **How to contribute**: [CONTRIBUTING.md](CONTRIBUTING.md)
   - Contribution process
   - Code style
   - PR guidelines
   - Review criteria

2. **Testing**: [TESTING.md](TESTING.md)
   - Validation process
   - Testing examples
   - Automated testing
   - CI integration

3. **Review history**: [CHANGELOG.md](CHANGELOG.md)
   - Version history
   - Feature additions
   - Breaking changes

## By Topic

### Understanding the Framework

- **Core concepts**: [CONVENTIONS.md](CONVENTIONS.md#core-concepts)
- **Color scheme**: [CONVENTIONS.md](CONVENTIONS.md#color-scheme)
- **Layout options**: [CONVENTIONS.md](CONVENTIONS.md#layout-and-organization)
- **Best practices**: [CONVENTIONS.md](CONVENTIONS.md#best-practices)

### Creating Diagrams

- **First diagram**: [GETTING_STARTED.md](GETTING_STARTED.md#step-4-create-your-first-diagram)
- **Common patterns**: [QUICK_REFERENCE.md](QUICK_REFERENCE.md#quick-patterns)
- **Templates**: [templates/](templates/)
- **Examples**: [examples/](examples/)

### Specific Scenarios

- **Linear history**: [examples/linear-history.d2](examples/linear-history.d2)
- **Branching**: [examples/branching.d2](examples/branching.d2)
- **Merging**: [examples/merge-commits.d2](examples/merge-commits.d2)
- **Conflicts**: [examples/conflict-scenario.d2](examples/conflict-scenario.d2)
- **Rebasing**: [examples/rebase-scenario.d2](examples/rebase-scenario.d2)
- **Complex graphs**: [examples/complex-graph.d2](examples/complex-graph.d2)

### Styling and Theming

- **Default theme**: [styles/default-theme.d2](styles/default-theme.d2)
- **Classes**: [QUICK_REFERENCE.md](QUICK_REFERENCE.md#common-classes)
- **Colors**: [QUICK_REFERENCE.md](QUICK_REFERENCE.md#color-reference)
- **Custom styling**: [README.md](README.md#advanced-features)

### Technical Reference

- **Node types**: [CONVENTIONS.md](CONVENTIONS.md#nodes-commitschangesets)
- **Edge types**: [CONVENTIONS.md](CONVENTIONS.md#edges-parent-child-relationships)
- **Branch pointers**: [CONVENTIONS.md](CONVENTIONS.md#branchesreferences)
- **Special states**: [CONVENTIONS.md](CONVENTIONS.md#special-states)

## Examples by Complexity

### Beginner
- [linear-history.d2](examples/linear-history.d2) - Simple chain
- [basic-commit.d2](templates/basic-commit.d2) - Single commit

### Intermediate
- [branching.d2](examples/branching.d2) - Multiple branches
- [merge-commits.d2](examples/merge-commits.d2) - Merge operations
- [branch-pointer.d2](templates/branch-pointer.d2) - Branch references

### Advanced
- [complex-graph.d2](examples/complex-graph.d2) - Multi-branch scenario
- [conflict-scenario.d2](examples/conflict-scenario.d2) - Conflict states
- [rebase-scenario.d2](examples/rebase-scenario.d2) - Before/after rebase

## External Resources

- [D2 Language Documentation](https://d2lang.com/)
- [D2 Playground](https://play.d2lang.com/) - Test online
- [JJ (Jujutsu) Documentation](https://github.com/martinvonz/jj)
- [JJ Tutorial](https://steveklabnik.github.io/jujutsu-tutorial/)

## Quick Navigation

```
📁 D2-jj/
├── 📄 README.md                    ← Start here
├── 📄 GETTING_STARTED.md           ← Tutorial
├── 📄 QUICK_REFERENCE.md           ← Quick lookup
├── 📄 CONVENTIONS.md               ← Complete guide
├── 📄 USAGE_EXAMPLES.md            ← Real scenarios
├── 📄 TESTING.md                   ← Testing guide
├── 📄 CONTRIBUTING.md              ← How to contribute
├── 📄 CHANGELOG.md                 ← Version history
├── 📄 INDEX.md                     ← This file
│
├── 📁 examples/                    ← Working examples
│   ├── linear-history.d2
│   ├── branching.d2
│   ├── merge-commits.d2
│   ├── complex-graph.d2
│   ├── conflict-scenario.d2
│   └── rebase-scenario.d2
│
├── 📁 styles/                      ← Themes
│   └── default-theme.d2
│
└── 📁 templates/                   ← Starter templates
    ├── basic-commit.d2
    └── branch-pointer.d2
```

## Getting Help

- **Start with**: [README.md](README.md) for overview
- **Follow**: [GETTING_STARTED.md](GETTING_STARTED.md) for tutorial
- **Reference**: [QUICK_REFERENCE.md](QUICK_REFERENCE.md) for patterns
- **Learn**: [USAGE_EXAMPLES.md](USAGE_EXAMPLES.md) for scenarios
- **Master**: [CONVENTIONS.md](CONVENTIONS.md) for details

## Search Tips

- Looking for colors? → [QUICK_REFERENCE.md](QUICK_REFERENCE.md#color-reference)
- Need a pattern? → [QUICK_REFERENCE.md](QUICK_REFERENCE.md#quick-patterns)
- Want an example? → [examples/](examples/)
- Need conventions? → [CONVENTIONS.md](CONVENTIONS.md)
- How to contribute? → [CONTRIBUTING.md](CONTRIBUTING.md)

---

**Have a question not covered here?** Open an issue on GitHub!
