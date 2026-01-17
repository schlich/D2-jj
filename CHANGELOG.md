# Changelog

All notable changes to the D2-jj framework will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [1.0.0] - 2026-01-17

### Added

#### Core Framework
- Complete D2 conventions for representing JJ commit graphs
- Standardized color scheme for visual consistency
- Node conventions for commits, branches, and references
- Edge conventions for parent-child relationships
- Layout guidelines (vertical and horizontal)

#### Documentation
- `README.md` - Comprehensive overview and quick start guide
- `CONVENTIONS.md` - Detailed framework conventions and best practices
- `GETTING_STARTED.md` - Step-by-step tutorial for new users
- `QUICK_REFERENCE.md` - Quick reference for common patterns
- `USAGE_EXAMPLES.md` - Real-world usage scenarios
- `TESTING.md` - Testing and validation guide
- `CONTRIBUTING.md` - Contribution guidelines

#### Styles
- `styles/default-theme.d2` - Default theme with reusable class definitions
  - Commit classes (normal, immutable, conflict)
  - Branch pointer classes (main, feature, bookmark)
  - Working copy class
  - Note/annotation class

#### Examples
- `examples/linear-history.d2` - Simple linear commit history
- `examples/branching.d2` - Multiple diverging branches
- `examples/merge-commits.d2` - Merge commit with two parents
- `examples/complex-graph.d2` - Complex multi-branch scenario
- `examples/conflict-scenario.d2` - Conflicted commit visualization
- `examples/rebase-scenario.d2` - Rebase operation before/after

#### Templates
- `templates/basic-commit.d2` - Single commit template
- `templates/branch-pointer.d2` - Branch reference template

#### Project Files
- `.gitignore` - Ignore patterns for output files

### Features

#### Visual Elements
- Commit nodes as rounded rectangles
- Branch pointers as colored hexagons
- Working copy indicator as orange circle
- Color-coded states (immutable, conflict, etc.)
- Support for annotations and notes

#### Graph Patterns
- Linear histories
- Parallel branches
- Merge commits
- Conflict states
- Rebase operations
- Multiple working copies

#### Conventions
- Consistent color scheme across all elements
- Directional flow (child to parent)
- Class-based styling system
- Theme import mechanism
- Modular and composable structure

### Design Decisions

- **Vertical Layout**: Chosen as default to match `jj log` output
- **Child → Parent**: Edge direction for consistency with Git/JJ
- **Hexagons for Branches**: Distinct shape to differentiate from commits
- **Color Coding**: Intuitive colors (green=main, blue=feature, orange=current)
- **Class-Based**: Enables easy customization and theme variants

### Documentation Philosophy

- **Progressive Disclosure**: Start simple, add complexity gradually
- **Learning by Example**: Extensive examples for common scenarios
- **Quick Reference**: Fast lookup for experienced users
- **Comprehensive Guide**: Detailed conventions for edge cases

## Future Considerations

Potential additions for future versions:

- Additional themes (dark mode, color-blind friendly)
- More complex graph examples
- Integration examples with JJ commands
- Animated/interactive diagram examples
- Advanced patterns (octopus merges, etc.)
- Automated diagram generation tools

## Links

- Repository: https://github.com/schlich/D2-jj
- D2 Documentation: https://d2lang.com/
- JJ Documentation: https://github.com/martinvonz/jj
