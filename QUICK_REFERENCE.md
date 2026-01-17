# D2-jj Quick Reference

Quick reference guide for common patterns and conventions.

## Basic Structure

```d2
# Import default theme
...@styles/default-theme.d2

# Set direction
direction: up

# Define commits
commit_id: {
  label: "change_id\nMessage"
  class: commit
}

# Define relationships
child -> parent
```

## Common Classes

| Class | Usage |
|-------|-------|
| `commit` | Normal mutable commit |
| `commit-immutable` | Pushed/immutable commit (gray) |
| `commit-conflict` | Conflicted commit (red border) |
| `branch-main` | Main branch pointer (green) |
| `branch-feature` | Feature branch pointer (blue) |
| `working-copy` | Working copy indicator (@) (orange) |
| `bookmark` | Bookmark/tag pointer (purple) |
| `note` | Text annotation |

## Quick Patterns

### Single Commit
```d2
my_commit: {
  label: "abc123\nCommit message"
  class: commit
}
```

### Linear History
```d2
c3 -> c2
c2 -> c1
c1 -> c0
```

### Branch
```d2
feature: {
  label: "feature-name"
  class: branch-feature
}
feature -> commit_id
```

### Working Copy
```d2
wc: {
  label: "@"
  class: working-copy
}
wc -> current_commit
```

### Merge (Two Parents)
```d2
merge -> parent1
merge -> parent2
```

### Conflict
```d2
conflict: {
  label: "abc123\n⚠ CONFLICT"
  class: commit-conflict
}
```

## Layout Options

```d2
direction: up      # Bottom to top (default)
direction: down    # Top to bottom
direction: right   # Left to right
direction: left    # Right to left
```

## Color Reference

```
Main:     #4CAF50 (Green)
Feature:  #2196F3 (Blue)
Working:  #FF9800 (Orange)
Bookmark: #9C27B0 (Purple)
Conflict: #F44336 (Red)
Immut:    #E0E0E0 (Gray)
```

## Rendering

```bash
# Basic render
d2 input.d2 output.svg

# PNG output
d2 input.d2 output.png

# With theme
d2 --theme=0 input.d2 output.svg

# Watch mode
d2 --watch input.d2 output.svg
```

## Common Workflows

### Document Current State
1. Run `jj log --graph`
2. Identify key commits and relationships
3. Create D2 file with structure
4. Add branch pointers and working copy
5. Render and review

### Explain Merge Strategy
1. Identify merge commit and parents
2. Show branches leading to merge
3. Highlight the merge point
4. Add notes explaining strategy

### Illustrate Feature Work
1. Show base commit
2. Add feature branch diverging
3. Show feature commits
4. Add branch pointer and @
5. Optionally show future merge

## Tips

- Use short change IDs (8 chars) for readability
- Keep commit messages concise in labels
- Add notes for complex scenarios
- Use consistent direction throughout
- Minimize edge crossings
- Group related commits in containers
- Add legends for color meanings in complex diagrams
