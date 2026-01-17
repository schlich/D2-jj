# Usage Examples

Real-world scenarios and use cases for the D2-jj framework.

## Scenario 1: Documenting a Feature Branch Workflow

You want to document how feature branches are developed and merged in your project.

```d2
...@styles/default-theme.d2

direction: up

# Main branch history
main_1: {
  label: "abc1234\nInitial release"
  class: commit-immutable
}

main_2: {
  label: "def5678\nBug fixes"
  class: commit-immutable
}

main_3: {
  label: "ghi9012\nMerge feature"
  class: commit-immutable
}

# Feature development
feat_1: {
  label: "jkl3456\nStart feature"
  class: commit-immutable
}

feat_2: {
  label: "mno7890\nImplement core"
  class: commit-immutable
}

feat_3: {
  label: "pqr1234\nAdd tests"
  class: commit-immutable
}

# Relationships
main_2 -> main_1
feat_1 -> main_1
feat_2 -> feat_1
feat_3 -> feat_2
main_3 -> main_2
main_3 -> feat_3

# Branch pointers
main: {
  label: "main"
  class: branch-main
}
main -> main_3

# Notes
workflow: "Feature branch workflow:\n1. Branch from main\n2. Develop feature\n3. Merge back to main" {
  class: note
}
```

## Scenario 2: Explaining a Rebase Operation

Show team members how rebasing works in JJ.

```d2
...@styles/default-theme.d2

direction: up

# Old state
old_main: {
  label: "old123\nOld main"
  class: commit-immutable
  style.opacity: 0.5
}

old_feat: {
  label: "old456\nOld feature"
  class: commit-immutable
  style.opacity: 0.5
}

old_feat -> old_main: {
  style.opacity: 0.3
  style.stroke-dash: 5
}

# New state
new_main_1: {
  label: "new123\nMain update 1"
  class: commit-immutable
}

new_main_2: {
  label: "new456\nMain update 2"
  class: commit-immutable
}

new_feat: {
  label: "new789\nRebased feature"
  class: commit
}

new_main_1 -> old_main
new_main_2 -> new_main_1
new_feat -> new_main_2

# Annotations
rebase_label: "jj rebase -d new456" {
  class: note
  style.font-color: "#2196F3"
  style.bold: true
}
```

## Scenario 3: Tracking Multiple Parallel Features

Visualize concurrent feature development.

```d2
...@styles/default-theme.d2

direction: up

base: {
  label: "base123\nCommon base"
  class: commit-immutable
}

# Feature A
feat_a: {
  label: "feata12\nFeature A"
  class: commit
}
feat_a -> base

# Feature B
feat_b: {
  label: "featb34\nFeature B"
  class: commit
}
feat_b -> base

# Feature C
feat_c: {
  label: "featc56\nFeature C"
  class: commit
}
feat_c -> base

# Branch pointers
br_a: {
  label: "feature-a"
  class: branch-feature
}
br_a -> feat_a

br_b: {
  label: "feature-b"
  class: branch-feature
}
br_b -> feat_b

br_c: {
  label: "feature-c"
  class: branch-feature
}
br_c -> feat_c

# Working copy on feature B
wc: {
  label: "@"
  class: working-copy
}
wc -> feat_b
```

## Scenario 4: Showing Release Branches

Document release and maintenance branches.

```d2
...@styles/default-theme.d2

direction: up

# Main development
v1_base: {
  label: "v1base\nStart 1.0"
  class: commit-immutable
}

v1_release: {
  label: "v1rel\nRelease 1.0"
  class: commit-immutable
}

v1_hotfix: {
  label: "v1fix\nHotfix 1.0.1"
  class: commit-immutable
}

# Continued main development
v2_work: {
  label: "v2work\nStart 2.0"
  class: commit-immutable
}

v2_features: {
  label: "v2feat\n2.0 features"
  class: commit
}

# Relationships
v1_release -> v1_base
v1_hotfix -> v1_release
v2_work -> v1_release
v2_features -> v2_work

# Version tags
v1_0: {
  label: "v1.0"
  class: bookmark
}
v1_0 -> v1_release

v1_0_1: {
  label: "v1.0.1"
  class: bookmark
}
v1_0_1 -> v1_hotfix

# Branches
rel_1_0: {
  label: "release-1.0"
  class: branch-feature
}
rel_1_0 -> v1_hotfix

main: {
  label: "main"
  class: branch-main
}
main -> v2_features

wc: {
  label: "@"
  class: working-copy
}
wc -> v2_features
```

## Scenario 5: Illustrating Conflict Resolution

Show the process of resolving conflicts.

```d2
...@styles/default-theme.d2

direction: up

base: {
  label: "base123\nCommon base"
  class: commit-immutable
}

change_a: {
  label: "chga456\nChange A"
  class: commit-immutable
}

change_b: {
  label: "chgb789\nChange B"
  class: commit-immutable
}

conflict: {
  label: "conf012\n⚠ CONFLICT"
  class: commit-conflict
}

resolved: {
  label: "rslv345\nResolved"
  class: commit
}

# Relationships
change_a -> base
change_b -> base
conflict -> change_a
conflict -> change_b
resolved -> conflict

# Current state
wc: {
  label: "@"
  class: working-copy
}
wc -> resolved

# Process notes
steps: "Resolution steps:\n1. jj log (see conflict)\n2. jj resolve\n3. jj commit (if needed)" {
  class: note
}
```

## Scenario 6: Exploring History Before/After Change

Document the effect of history editing operations.

```d2
...@styles/default-theme.d2

direction: up

# Original history
orig_1: {
  label: "orig1\nCommit 1"
  class: commit-immutable
  style.opacity: 0.4
}

orig_2: {
  label: "orig2\nBad commit"
  class: commit-immutable
  style.opacity: 0.4
  style.stroke: "#F44336"
}

orig_3: {
  label: "orig3\nCommit 3"
  class: commit-immutable
  style.opacity: 0.4
}

orig_2 -> orig_1: {
  style.opacity: 0.3
  style.stroke-dash: 5
}
orig_3 -> orig_2: {
  style.opacity: 0.3
  style.stroke-dash: 5
}

# New history (after abandoning bad commit)
new_1: {
  label: "new1\nCommit 1"
  class: commit-immutable
}

new_3: {
  label: "new3\nCommit 3 (rebased)"
  class: commit
}

new_3 -> new_1

# Labels
before: "Before: jj abandon orig2" {
  class: note
  style.opacity: 0.6
}

after: "After: Bad commit removed,\nhistory simplified" {
  class: note
}
```

## Scenario 7: Multiple Working Copies

JJ's unique ability to have multiple working copies.

```d2
...@styles/default-theme.d2

direction: up

main_commit: {
  label: "main123\nMain work"
  class: commit-immutable
}

wc_main: {
  label: "@ main"
  class: working-copy
}
wc_main -> main_commit

feature_commit: {
  label: "feat456\nFeature work"
  class: commit
}
feature_commit -> main_commit

wc_feature: {
  label: "@ feature"
  shape: circle
  style.fill: "#FF9800"
  style.font-color: "#FFFFFF"
  width: 60
  height: 50
}
wc_feature -> feature_commit

note: "Multiple working copies:\nmain workspace and feature workspace\nactive simultaneously" {
  class: note
}
```

## Tips for Creating Your Own

1. **Start Simple**: Begin with basic structure, add details later
2. **Use Templates**: Copy from examples/ and modify
3. **Iterate**: Render frequently to catch issues early
4. **Keep Labels Short**: Use brief commit messages
5. **Add Context**: Use notes to explain the scenario
6. **Show States**: Use opacity/dashing for before/after
7. **Be Consistent**: Follow the color scheme and conventions
8. **Test**: Verify the diagram clearly communicates your point

## Common Patterns

### Sequential Development
```d2
newest -> newer -> new -> old
```

### Parallel Branches
```d2
branch_a -> base
branch_b -> base
branch_c -> base
```

### Merge and Continue
```d2
post_merge -> merge
merge -> branch_1
merge -> branch_2
```

### Rebase Chain
```d2
rebased_3 -> rebased_2 -> rebased_1 -> new_base
```

### Abandoned Changes
```d2
kept: {
  label: "Kept"
  class: commit
}

abandoned: {
  label: "Abandoned"
  class: commit
  style.opacity: 0.3
  style.stroke-dash: 5
}
```
