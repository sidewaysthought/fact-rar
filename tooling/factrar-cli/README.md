# factrar-cli (proposed)

This directory is a placeholder for a future reference CLI implementation.

## Proposed UX

```bash
# Validate a file
factrar lint knowledge.frar

# Normalize to canonical form
factrar normalize knowledge.frar > knowledge.norm.frar

# Compare semantic changes across revisions
factrar diff old.frar new.frar --format md

# Show density stats with readable explanations
factrar stats knowledge.frar
```

## Design Principle
Tooling should make Fact-RAR **easier for humans to trust, review, and automate**, without changing its primary role as a semantic-packing language for cross-model transfer.
