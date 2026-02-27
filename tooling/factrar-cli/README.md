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

# Show density stats
factrar stats knowledge.frar
```

## Design Principle
Tooling should make Fact-RAR **easier to trust and automate**, without changing its primary role as a semantic-packing language for cross-model transfer.
