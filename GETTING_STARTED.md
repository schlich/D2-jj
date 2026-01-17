# Getting Started with D2-jj

A step-by-step guide to start using the D2-jj framework for visualizing JJ commit graphs.

## What You'll Learn

- How to install the required tools
- How to create your first D2 diagram of a JJ graph
- How to customize diagrams for your needs
- Best practices for clear visualizations

## Prerequisites

- Basic understanding of version control concepts
- Familiarity with JJ (Jujutsu) or similar VCS
- Text editor of your choice

## Step 1: Install D2

D2 is a diagram scripting language. Install it using your package manager:

### macOS
```bash
brew install d2
```

### Linux
```bash
curl -fsSL https://d2lang.com/install.sh | sh -s --
```

### Windows
```bash
scoop install d2
```

### Verify Installation
```bash
d2 --version
```

## Step 2: Clone or Download D2-jj

Get the D2-jj framework:

```bash
git clone https://github.com/schlich/D2-jj.git
cd D2-jj
```

Or download and extract the ZIP file from GitHub.

## Step 3: Explore Examples

Look at the provided examples:

```bash
# List available examples
ls examples/

# View an example file
cat examples/linear-history.d2

# Render an example
d2 examples/linear-history.d2 my-first-diagram.svg

# Open the SVG in your browser or image viewer
open my-first-diagram.svg  # macOS
xdg-open my-first-diagram.svg  # Linux
start my-first-diagram.svg  # Windows
```

## Step 4: Create Your First Diagram

Let's create a simple diagram of a JJ repository:

### 4.1: Create a New File

Create a file called `my-graph.d2`:

```d2
# Import the default theme
...@styles/default-theme.d2

# Set direction (commits flow upward)
direction: up

# Define commits
first_commit: {
  label: "abc1234\nInitial commit"
  class: commit-immutable
}

second_commit: {
  label: "def5678\nAdd feature"
  class: commit
}

# Define relationship (child -> parent)
second_commit -> first_commit

# Add main branch pointer
main: {
  label: "main"
  class: branch-main
}
main -> second_commit

# Add working copy indicator
wc: {
  label: "@"
  class: working-copy
}
wc -> second_commit
```

### 4.2: Render Your Diagram

```bash
d2 my-graph.d2 my-graph.svg
```

### 4.3: View Your Diagram

Open `my-graph.svg` in your browser or image viewer.

## Step 5: Customize Your Diagram

### Add More Commits

```d2
third_commit: {
  label: "ghi9012\nFix bug"
  class: commit
}

third_commit -> second_commit
```

### Add a Feature Branch

```d2
feature_commit: {
  label: "jkl3456\nNew feature"
  class: commit
}

feature_commit -> second_commit

feature_branch: {
  label: "feature-x"
  class: branch-feature
}
feature_branch -> feature_commit
```

### Show a Merge

```d2
merge_commit: {
  label: "mno7890\nMerge feature-x"
  class: commit
}

# Merge has two parents
merge_commit -> third_commit
merge_commit -> feature_commit
```

## Step 6: Use Different Layouts

Try different directions:

```d2
# Horizontal layout (left to right)
direction: right

# Horizontal layout (right to left)
direction: left

# Vertical layout (top to bottom)
direction: down

# Vertical layout (bottom to top) - default
direction: up
```

## Step 7: Match Your JJ Repository

To create a diagram of your actual JJ repository:

### 7.1: View Your JJ Log

```bash
jj log --graph
```

You'll see something like:
```
@  mzvwutvl you@example.com 2024-01-15 12:34:56 feature-x
│  Feature implementation
◉  yostqsxw you@example.com 2024-01-15 10:20:30 main
│  Bug fix
◉  rlvkpnrz you@example.com 2024-01-14 15:45:12
│  Initial commit
◉  qpvuntsm you@example.com 2024-01-14 14:00:00
   Root commit
```

### 7.2: Map to D2

Create your diagram:

```d2
...@styles/default-theme.d2

direction: up

qpvuntsm: {
  label: "qpvuntsm\nRoot commit"
  class: commit-immutable
}

rlvkpnrz: {
  label: "rlvkpnrz\nInitial commit"
  class: commit-immutable
}

yostqsxw: {
  label: "yostqsxw\nBug fix"
  class: commit-immutable
}

mzvwutvl: {
  label: "mzvwutvl\nFeature implementation"
  class: commit
}

rlvkpnrz -> qpvuntsm
yostqsxw -> rlvkpnrz
mzvwutvl -> yostqsxw

main: {
  label: "main"
  class: branch-main
}
main -> yostqsxw

feature_x: {
  label: "feature-x"
  class: branch-feature
}
feature_x -> mzvwutvl

wc: {
  label: "@"
  class: working-copy
}
wc -> mzvwutvl
```

## Step 8: Learn More

### Explore Advanced Features

- **Conflict visualization**: See `examples/conflict-scenario.d2`
- **Rebase operations**: See `examples/rebase-scenario.d2`
- **Complex graphs**: See `examples/complex-graph.d2`

### Read the Documentation

- [CONVENTIONS.md](CONVENTIONS.md) - Complete framework conventions
- [QUICK_REFERENCE.md](QUICK_REFERENCE.md) - Quick reference guide
- [USAGE_EXAMPLES.md](USAGE_EXAMPLES.md) - Real-world scenarios
- [TESTING.md](TESTING.md) - Testing and validation guide

### Use Templates

Start with templates for common patterns:

```bash
# Copy a template
cp templates/basic-commit.d2 my-custom-diagram.d2

# Edit and render
d2 my-custom-diagram.d2 output.svg
```

## Common Workflows

### Document a Merge Strategy

1. Identify the commits involved
2. Create commit nodes for each
3. Add relationships showing parents
4. Highlight the merge commit
5. Add notes explaining the strategy

### Explain a Rebase to Your Team

1. Show the original state (faded)
2. Show the new state (normal)
3. Use opacity to distinguish before/after
4. Add explanatory notes
5. Show the rebase command used

### Track Parallel Feature Work

1. Create commit nodes for each feature
2. Show common base commit
3. Add branch pointers for each feature
4. Indicate which is the working copy
5. Add status notes

## Tips for Success

1. **Start Simple**: Begin with basic structure, add complexity gradually
2. **Render Often**: Check your work frequently to catch errors early
3. **Use Consistent Styles**: Stick to the framework conventions
4. **Add Context**: Use notes to explain complex scenarios
5. **Keep Labels Short**: Use brief, clear commit messages
6. **Test Readability**: Ensure diagrams are easy to understand

## Troubleshooting

### "File not found" error for styles

Make sure your relative path is correct:
```d2
# If your file is in the root directory
...@styles/default-theme.d2

# If your file is in a subdirectory
...@../styles/default-theme.d2
```

### Commits appear in wrong order

Check your edge directions:
```d2
# Correct: child -> parent
child_commit -> parent_commit

# Incorrect: parent -> child (backwards)
parent_commit -> child_commit
```

### Styling not applied

Verify:
1. Theme file is imported
2. Class names match exactly
3. No typos in class attributes

### Diagram too cluttered

Strategies:
1. Focus on key commits only
2. Use opacity for less important elements
3. Group related commits in containers
4. Simplify labels
5. Break into multiple diagrams

## Next Steps

- Create diagrams for your own repositories
- Customize the theme to match your preferences
- Share diagrams with your team
- Contribute examples or improvements

## Getting Help

- Review the [CONVENTIONS.md](CONVENTIONS.md) for detailed guidelines
- Check [USAGE_EXAMPLES.md](USAGE_EXAMPLES.md) for scenarios
- Use the [D2 Playground](https://play.d2lang.com/) to test
- Read [D2 documentation](https://d2lang.com/) for D2 features
- Consult [JJ documentation](https://github.com/martinvonz/jj) for JJ concepts

Happy diagramming! 🎨
