# Proposal 0002: Reference Tooling + CLI Surface

## Status
Draft

## Motivation
Fact-RAR is easy to prototype in prompts, but adoption increases when users can validate and normalize artifacts locally with repeatable tooling.

## Goal
Define a minimal reference tooling surface that keeps the language lightweight while making workflows deterministic.

## Non-goals
- Not replacing LLM-based encoding.
- Not forcing a single runtime or package ecosystem.
- Not requiring canonical mode for casual use.

## Proposed CLI Commands

```bash
factrar encode   # assistive encode pipeline (optional LLM adapter hooks)
factrar decode   # expand to plain-language propositions
factrar lint     # syntax + style checks
factrar normalize# canonicalization profile output
factrar diff     # semantic diff between two Fact-RAR files
factrar stats    # token/proposition density metrics
```

## Minimal I/O Contract
- Input: UTF-8 `.frar` or plain text
- Output: Fact-RAR text, JSON AST, or markdown report (`--format text|json|md`)
- Exit codes:
  - `0` success
  - `1` lint/validation failures
  - `2` parser/runtime error

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
- Should benchmark output format be JSONL by default?
