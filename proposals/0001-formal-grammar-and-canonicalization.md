# Proposal 0001: Formal Grammar + Canonicalization for Fact-RAR

## Status
Draft

## Motivation
Fact-RAR already has a practical, readable spec that works well for prompt-driven use. Adding a formal grammar and canonicalization profile would make independent implementations easier to align and would unlock more deterministic tooling (linting, normalization, diffing).

## Goal
Define a machine-testable grammar and a canonicalization profile so two implementations can parse and normalize equivalent statements to the same output.

## Non-goals
- Not changing Fact-RAR's core objective (semantic packing for LLM transfer).
- Not requiring users to write in canonical form manually.
- Not forcing a single tokenizer/model implementation.

## Draft Grammar (EBNF, v0)

```ebnf
line            = [query] (conditional | with_block | clause) ;
query           = "?" ;

conditional     = "if" , condition , ":" , clause ;
condition       = expr ;

with_block      = "with" , subject , ":" , newline , indented_clause , {newline , indented_clause} ;
indented_clause = clause ;

clause          = subject , ws , predicate , [ws , object] , [ws , time_marker] ;
predicate       = [negation] , verb , [modality] ;

subject         = atom | set | list ;
object          = atom | set | list | kv ;

set             = "{" , value , {"," , value} , "}" ;
list            = "[" , value , {"," , value} , "]" ;
kv              = atom , ":" , value ;

expr            = value , comparator , value ;
comparator      = "<" | ">" | "<=" | ">=" | "==" ;

value           = atom | set | list | kv ;
atom            = token , {("." | "_" | "-") , token} ;
verb            = atom ;

negation        = "!" | "¬" ;
modality        = "?" | "!" | "!!" ;

time_marker     = duration_future | exact_past | imperfect ;
duration_future = "+" , duration ;
exact_past      = "-" , iso_datetime ;
imperfect       = verb , "~" ;

ws              = " " , {" "} ;
newline         = "\n" ;
```

## Canonicalization Profile (Draft)
1. Normalize whitespace to single spaces between major terms.
2. Sort unordered sets `{}` lexicographically; preserve list `[]` order.
3. Preserve source casing only when needed; default to lowercase atoms.
4. Normalize negation to `!` (convert `¬` -> `!`).
5. Prefer explicit `noun:[value unit]` over mixed ad-hoc quantity forms in normalized output.
6. Keep one clause per line after expansion of `with` blocks for machine export mode.
7. Preserve semantic-equivalent operator forms (`<=`, `>=`, etc.) exactly as written.
8. Emit stable key order for nested structures to support deterministic diffing.

## Reference Tests (Proposed)
- Parse acceptance: valid examples from README and sample corpora.
- Parse rejection: malformed separators, invalid nesting, invalid comparators.
- Round-trip: parse -> normalize -> parse stability.
- Equivalence: multiple surface forms normalize to same canonical output.

## Rollout Plan
- Phase 1: publish grammar + examples + open discussion.
- Phase 2: add canonicalization profile and test vectors.
- Phase 3: mark profile as recommended for tools/benchmarks.

## Open Questions
- Should canonical mode require lowercase atoms globally?
- Should `with` remain a first-class syntax in canonical output or always expand?
- Should provenance/confidence metadata be in-band or sidecar?
