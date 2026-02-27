# Proposal 0002: Reference Tooling + CLI Surface

## Status
Draft

## Motivation
Fact-RAR is easy to prototype in prompts, but adoption increases when humans can validate, compare, and trust artifacts locally with repeatable tooling.

## Goal
Define a minimal reference tooling surface that keeps the language lightweight while making workflows deterministic and understandable to human contributors.

## Non-goals
- Not replacing LLM-based encoding.
- Not forcing a single runtime or package ecosystem.
- Not requiring canonical mode for casual use.

## Proposed CLI Commands

```bash
factrar encode    # assistive encode pipeline (optional LLM adapter hooks)
factrar decode    # expand to plain-language propositions for human review
factrar lint      # syntax + style checks with readable diagnostics
factrar normalize # canonicalization profile output for consistency
factrar diff      # semantic diff between two Fact-RAR files (change summary)
factrar stats     # human-readable density/clarity metrics report
```

## Minimal I/O Contract
- Input: UTF-8 `.frar` or plain text
- Output: Fact-RAR text, JSON AST, or markdown report (`--format text|json|md`)
- Exit codes:
  - `0` success
  - `1` lint/validation failures
  - `2` parser/runtime error

## Human-First Output Defaults (Proposed)
- Default output should be concise text/markdown that a non-implementer can read quickly.
- Machine formats (JSON/AST) should be opt-in via `--format json`.
- `factrar stats` should explain *why* a score changed (for example: more clauses, fewer ambiguities, improved consistency), not only print raw numbers.

## Initial Lint Rules (Draft)
1. One clause per line unless in a `with` block.
2. Flag pronouns in canonical mode.
3. Warn on ambiguous nested sets/lists.
4. Warn when both `!` and `¬` appear in same document.
5. Warn on missing explicit subjects in multi-line blocks.

## Adoption Plan
- Phase 1: parser + lint + normalize
- Phase 2: diff + stats
- Phase 3: optional encode/decode adapters and benchmark harness hooks

## Open Questions
- Should semantic diff rely on normalized AST only?
- Should `encode` be plugin-based to support multiple model providers?
- Should the default reporting profile prioritize human-readable markdown over JSONL?
