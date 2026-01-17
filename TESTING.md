# Testing Guide

This guide explains how to test and validate the D2-jj framework.

## Prerequisites

Install D2:

```bash
# macOS
brew install d2

# Linux
curl -fsSL https://d2lang.com/install.sh | sh -s --

# Windows
scoop install d2
```

## Testing Examples

### Basic Validation

Test each example file renders without errors:

```bash
# Test linear history
d2 examples/linear-history.d2 test-outputs/linear-history.svg

# Test branching
d2 examples/branching.d2 test-outputs/branching.svg

# Test merge commits
d2 examples/merge-commits.d2 test-outputs/merge-commits.svg

# Test complex graph
d2 examples/complex-graph.d2 test-outputs/complex-graph.svg

# Test conflict scenario
d2 examples/conflict-scenario.d2 test-outputs/conflict-scenario.svg

# Test rebase scenario
d2 examples/rebase-scenario.d2 test-outputs/rebase-scenario.svg
```

### Automated Testing

Use this script to test all examples:

```bash
#!/bin/bash
# test-all.sh

mkdir -p test-outputs

examples=(
  "linear-history"
  "branching"
  "merge-commits"
  "complex-graph"
  "conflict-scenario"
  "rebase-scenario"
)

echo "Testing D2-jj examples..."
failed=0

for example in "${examples[@]}"; do
  echo "Testing examples/${example}.d2..."
  if d2 "examples/${example}.d2" "test-outputs/${example}.svg" 2>&1; then
    echo "✓ ${example} rendered successfully"
  else
    echo "✗ ${example} failed to render"
    ((failed++))
  fi
done

if [ $failed -eq 0 ]; then
  echo ""
  echo "✓ All examples passed!"
  echo "Check test-outputs/ for generated diagrams"
  exit 0
else
  echo ""
  echo "✗ ${failed} example(s) failed"
  exit 1
fi
```

Save as `test-all.sh` and run:

```bash
chmod +x test-all.sh
./test-all.sh
```

## Visual Inspection

After rendering, visually inspect each diagram to verify:

1. **Layout**: Commits flow in the correct direction
2. **Relationships**: Edges connect the right nodes
3. **Styling**: Colors and shapes match conventions
4. **Labels**: Text is readable and accurate
5. **Clarity**: Diagram is easy to understand

## Testing Custom Diagrams

When creating your own diagrams:

1. Start with a template or example
2. Make incremental changes
3. Render frequently to catch errors early
4. Verify the output matches your intent
5. Check that styling is consistent

## Common Issues

### Import Path Errors

If you see `file not found` errors for styles:

```
Error: Could not read file: ../styles/default-theme.d2
```

Ensure the relative path is correct from your diagram's location.

### Syntax Errors

D2 will report line numbers for syntax errors:

```
Error: expected '}' at line 15
```

Check for:
- Missing braces
- Incorrect nesting
- Invalid property names
- Typos in class names

### Rendering Issues

If shapes or labels appear incorrect:
- Verify class names match those in default-theme.d2
- Check that the theme file is imported
- Ensure label text is properly quoted if it contains special characters

## Validation Checklist

- [ ] All examples render without errors
- [ ] Colors match the documented scheme
- [ ] Shapes are consistent across examples
- [ ] Labels are clear and readable
- [ ] Edges point in the correct direction
- [ ] Layout is logical and easy to follow
- [ ] Styles are applied correctly
- [ ] Notes and annotations are visible

## Online Testing

Use the [D2 Playground](https://play.d2lang.com/) to test diagrams online:

1. Copy your D2 code
2. Paste into the playground
3. View the rendered output
4. Debug any issues

**Note**: The playground may not support relative imports, so you may need to inline the styles.

## Performance Testing

For large graphs:

```bash
# Time the rendering
time d2 examples/complex-graph.d2 output.svg

# Test with different themes
d2 --theme=0 examples/complex-graph.d2 output-theme0.svg
d2 --theme=1 examples/complex-graph.d2 output-theme1.svg
```

## Continuous Integration

Example GitHub Actions workflow:

```yaml
name: Test D2-jj Examples

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Install D2
        run: |
          curl -fsSL https://d2lang.com/install.sh | sh -s --
          
      - name: Test examples
        run: |
          mkdir -p test-outputs
          for file in examples/*.d2; do
            echo "Testing $file"
            d2 "$file" "test-outputs/$(basename "$file" .d2).svg"
          done
          
      - name: Upload artifacts
        uses: actions/upload-artifact@v3
        with:
          name: rendered-diagrams
          path: test-outputs/
```

## Reporting Issues

When reporting issues with the framework:

1. Include the D2 version: `d2 --version`
2. Provide the failing .d2 file
3. Share the error message
4. Describe expected vs. actual behavior
5. Include rendered output if available
