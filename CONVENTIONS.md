# D2-jj Framework Conventions

A framework for visualizing JJ (Jujutsu) changeset and commit graphs using D2 diagrams.

## Overview

This framework provides conventions and best practices for representing JJ version control graphs in D2 format, enabling clear and consistent visualization of changesets, branches, and commit relationships.

## Core Concepts

### 1. Nodes (Commits/Changesets)

Commits/changesets are represented as shaped nodes with specific attributes:

```d2
commit_id: {
  label: "commit message"
  shape: rectangle
  style.border-radius: 5
}
```

**Conventions:**
- Use descriptive IDs matching JJ change IDs (e.g., `qpvuntsm`, `rlvkpnrz`)
- Include short commit message as label
- Use rectangles with rounded corners for consistency
- Height/width should be proportional to label content

### 2. Edges (Parent-Child Relationships)

Parent-child relationships are represented as directed edges:

```d2
child_commit -> parent_commit
```

**Conventions:**
- Direction flows from child to parent (upward in visual layout)
- Use solid lines for direct parent relationships
- Multiple parents indicate merge commits

### 3. Branches/References

Branches and bookmarks are represented as separate labeled nodes:

```d2
branch_main: {
  label: "main"
  shape: hexagon
  style.fill: "#4CAF50"
  style.font-color: "#FFFFFF"
}
branch_main -> commit_id
```

**Conventions:**
- Use hexagon shape for branch pointers
- Green fill (`#4CAF50`) for main/master branch
- Blue fill (`#2196F3`) for feature branches
- Orange fill (`#FF9800`) for working copy marker (@)
- Purple fill (`#9C27B0`) for bookmarks/tags

### 4. Special States

#### Working Copy (@)
```d2
working_copy: {
  label: "@"
  shape: circle
  style.fill: "#FF9800"
  style.font-color: "#FFFFFF"
}
```

#### Change States
- **Immutable commits**: Gray fill (`#E0E0E0`)
- **Mutable commits**: White/default fill
- **Conflicted commits**: Red border (`style.stroke: "#F44336"`)

### 5. Layout and Organization

**Vertical Layout** (recommended):
```d2
direction: up
```
- Child commits at bottom, parents flow upward
- Mimics traditional `jj log` output
- Most recent changes at bottom

**Horizontal Layout** (alternative):
```d2
direction: right
```
- Root commits on left, newer commits to the right
- Good for wide, shallow histories

### 6. Color Scheme

| Element | Color | Hex | Usage |
|---------|-------|-----|-------|
| Main branch | Green | `#4CAF50` | Primary development branch |
| Feature branch | Blue | `#2196F3` | Feature/topic branches |
| Working copy | Orange | `#FF9800` | Current working location |
| Tag/Bookmark | Purple | `#9C27B0` | Named references |
| Conflict | Red | `#F44336` | Conflicted states |
| Immutable | Gray | `#E0E0E0` | Pushed/immutable commits |

### 7. Annotations and Labels

Add explanatory notes using classes:

```d2
classes: {
  note: {
    shape: text
    style.font-size: 12
    style.italic: true
  }
}

explanation: "Merge commit" {
  class: note
}
```

## Example Patterns

### Linear History
```d2
direction: up
commit3 -> commit2
commit2 -> commit1
commit1 -> commit0
```

### Branching
```d2
direction: up
feature_commit -> base_commit
main_commit -> base_commit
```

### Merge Commit
```d2
direction: up
merge_commit -> feature_commit
merge_commit -> main_commit
```

## Best Practices

1. **Keep IDs short but meaningful**: Use JJ's short change IDs (8 chars)
2. **Consistent styling**: Apply the same styles throughout a diagram
3. **Clear labels**: Use concise commit messages
4. **Logical direction**: Maintain consistent edge direction
5. **Minimize crossing**: Arrange nodes to reduce edge crossings
6. **Use containers**: Group related commits in containers when needed
7. **Add legends**: Include color/shape legends for complex diagrams

## File Organization

```
examples/
  linear-history.d2         # Simple linear commit history
  branching.d2              # Multiple branches
  merge-commits.d2          # Merges and converging histories
  complex-graph.d2          # Real-world complex scenario
styles/
  default-theme.d2          # Reusable style definitions
templates/
  basic-commit.d2           # Template for single commit
  branch-pointer.d2         # Template for branch reference
```

## Rendering

Render D2 diagrams using the D2 CLI:

```bash
d2 input.d2 output.svg
d2 input.d2 output.png
d2 --theme=0 input.d2 output.svg  # Use specific theme
```

## References

- [D2 Documentation](https://d2lang.com/)
- [Jujutsu Documentation](https://github.com/martinvonz/jj)
- [D2 Playground](https://play.d2lang.com/)
