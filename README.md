# Fact-RAR

Fact-RAR is a mini-language that compresses domain knowledge into fewer tokens (sometimes by 70% or more), making system prompts cheaper and more precise in large language models..

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

## What is this?

Fact-RAR is a symbolic mini-language for writing declarative knowledge in an **LLM-friendly**, **token-efficient**, and **human-readable** format. (Some humans may find it tedious or dense.) It is inspired by Japanese grammar, low-resource syntax, and programming idioms.

## Getting Started

1. Copy-and-paste the specification below into your large language model.
2. Tell your large language model (GPT-4o, DeepSeek, Copilot, Gemini 2.5 Flash, LLaMA 4, etc.) to compress the knowledge using the specification.
3. After the LLM encodes your text, save it in a file, or paste it into another chat for use whenever you need it.

### Copy-and-Paste Specification To Use in Prompts (v 1.1)
```
Use the Fact-RAR specification to preserve information in a highly compressed format any LLM can understand.
- Sentence frame: `S V O` (1 clause per line)
- Word choice: shortest unambiguous term; keep `if`, `and`, `or` in English
- Grouped expressions: `{}` = subjects/conditionals, `[]` = verbs/objects (Python literal syntax)
  - Multiple statements: use `with` block  
  - Multiple details of subject: same `with` usage
- Pronouns: avoid; repeat noun or use synonym
- Time:
  - Present = default
  - Future: `+3d`, `+2h30m`
  - Exact past: `-2025-06-28T14:00-05`
  - Imperfect: `verb~`
- Negation: prefix `!` or `¬` → `cat !eat fish`
- Modality: `?` = possible, `!` = required, `!!` = urgent
- Relations: use as verb phrase → `book locate shelf`
- Attributes: ordered `[ ]`, unordered `{ }`
- Quantities: integer `×n` or `noun:n`, value+unit `noun:[value unit]`
- Comparatives: `<`, `>`, `<=`, `>=`, `==`
- Questions: prefix `?` → `?cat eat fish`
- Conditionals: `if rain heavy: window close!`
```

## The Idea
Give an LLM the specification, then ask it to encode your knowledge (such as an article, a syllabus, a technical standard, etc.) The LLM produces the "compressed knowledge" for use in a system prompt or a message.

If you give another LLM the compressed knowledge, it will be able to answer questions from the blob. It isn't necessary to give the destination LLM the specification. (Exceptionally small LLMs may strugge, so you may need to give it the specification before decoding.)

The purpose is not to preserve the input language. The purpose is to preserve the conveyed facts or knowledge. Encode world facts, logic rules, or situation models in fewer tokens without sacrificing clarity.

You can use it for:

* System prompts
* Context injection
* World modeling
* Prompt chaining

Models **can infer the structure** from examples—even if they don’t know the specification.

## Core Specification (v 1.1)

| Element                      | Rule                                                                                                                                               | Example                                         |
|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| **Sentence frame**           | One clause per line using `S V O`.                                                                                                                  | `tree cast shade`                               |
| **Word choice**              | Use shortest unambiguous term from any language. Keep `if`, `and`, `or` in English.                                                                | `心 break`                                       |
| **Grouped expressions**      | `{}` = multiple subjects or conditions<br>`[]` = multiple verbs or objects<br>Use Python literal syntax                                             | `{city, town} evacuate [people:[1e6], pets]`    |
| **Multiple statements**      | Use Python `with` block to group multiple clauses about a subject or verb.                                                                          | `with tree:\n  drop leaves\n  cast shade`       |
| **Pronouns / anaphora**      | Avoid pronouns. Repeat noun or use synonym.                                                                                                         | —                                               |
| **Time markers**             | Present = default<br>Future: `+3d`, `+2h30m`<br>Exact past: `-2025-06-28T14:00-05`<br>Imperfect: suffix `~`                                          | `storm cross gulf +12h`                         |
| **Negation**                 | Prefix `!` or `¬` to verb.                                                                                                                           | `cat !eat fish`                                 |
| **Modality / certainty**     | `?` = possible<br>`!` = required<br>`!!` = urgent                                                                                                    | `crew evacuate!`                                |
| **Relations / prepositions** | Use prepositions as verb phrases.                                                                                                                   | `book locate shelf`                             |
| **Attributes**               | Ordered: `[ ]`<br>Unordered: `{ }`                                                                                                                  | `tree [big, tall]`                              |
| **Quantities**               | Integer: `×n` or `noun:n`<br>Value + unit: `noun:[value unit]`                                                                                      | `soldier×5 march`<br>`forecast:[5d] unreliable` |
| **Comparatives**             | Use math operators: `<`, `>`, `<=`, `>=`, `==`                                                                                                      | `price_A < price_B`                             |
| **Questions**                | Prefix `?` to the line                                                                                                                               | `? storm weaken`                                |
| **Conditionals**             | Use Python-style conditionals                                                                                                                       | `if flood risk_high: city warn!`                |

## Examples

### A Short Example
```text
storm form gulf [warm_water]
if storm intensity>=cat5: city warn!
city evacuate {people:[1e6]}
storm landfall coast +18h
? storm weaken
```

This five-line block encodes:

* A storm forming in warm Gulf waters
* A conditional evacuation warning
* A population-level response
* A projected landfall time
* An uncertain weakening trend

### Additional Examples.
* [A part of Romeo and Juliet encoded by GPT-4o and decoded by DeepSeek-R1](https://github.com/sidewaysthought/fact-rar/blob/main/example-romei-and-juliet.md)

## Proposals

Design proposals are tracked in `proposals/`.

- [Proposal 0001: Formal Grammar + Canonicalization](./proposals/0001-formal-grammar-and-canonicalization.md)

## Contributing

Have a variant? Suggest a syntax tweak? Found a case where a model fumbles?

**Open an issue or submit a pull request.**
The more eyes on the grammar, the sharper it gets.

## License

[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) — commercial use allowed.  
Forks, translations, and improvements must preserve this license. Attribution required.

## Questions?

Ping the creator. Or better yet—try it, break it, and post what you learn.

## Citation

If you use Fact-RAR in your project, publication, or tool, please cite it as:

> Catarino David Delgado. *Fact-RAR: A Domain-Specific Language for Compressed Knowledge Representation in LLMs.* v1.0, 2025. [https://github.com/sidewaysthought/fact-rar](https://github.com/sidewaysthought/fact-rar)

### BibTeX

```bibtex
@misc{factrar2025,
  author = {Catarino David Delgado},
  title = {Fact-RAR: A Domain-Specific Language for Compressed Knowledge Representation in LLMs},
  year = {2025},
  version = {1.0},
  url = {https://github.com/sidewaysthought/fact-rar}
}
