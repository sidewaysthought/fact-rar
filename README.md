# Fact-RAR

A minimal, expressive, domain-specific language (DSL) designed for **ultra-dense knowledge encoding in LLM prompts**.

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

## What is this?

Fact-RAR is a symbolic mini-language for writing declarative knowledge in an **LLM-friendly**, **token-efficient**, and **human-readable** format. (Some humans may find it tedious or dense.) It is a mini-language which was inspired by Japanese grammar, low-resource syntax, and programming idioms and syntax.

## The idea
Give an LLM the specification, then ask it to encode your knowledge (such as an article, a syllabus, a technical standard, etc.) The LLM produces the "compressed knowledge" for use in a system prompt or a message.

If you give another LLM the compressed knowledge, it will be able to answer questions from the blob. It isn't necessary to give the destination LLM the specification. (Exceptionally small LLMs may strugge, so you may need to give it the specification before decoding.)

The purpose is not to preserve the input language. The purpose is to preserve the conveyed facts or knowledge. Encode world facts, logic rules, or situation models in fewer tokens without sacrificing clarity.

You can use it for:

* System prompts
* Context injection
* World modeling
* Prompt chaining

Models **can infer the structure** from examples—even if they don’t know the specification.

## Core Specification (v 1.0)

| Element                    | Rule                                                                                                                                         | Example                                              |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|
| **Sentence frame**         | One clause per line using **S V O**.                                                                                                         | `tree cast shade`                                    |
| **Time markers**           | Default = present<br>Future: `+3d`, `+2h30m`<br>Exact past: `-2025-06-28T14:00-05`<br>Imperfect: verb suffixed with `~`                     | `storm cross gulf +12h`                              |
| **Negation**               | Prefix `!` or `¬` to verb.                                                                                                                   | `cat !eat fish`                                      |
| **Modality / certainty**   | `?` = possible<br>`!` = certain/required<br>`!!` = urgent imperative                                                                         | `crew evacuate!`                                     |
| **Relations / prepositions** | Use prepositions as verbs or verb phrases.                                                                                                | `book locate shelf`                                  |
| **Attributes**             | Ordered: `[ ]`<br>Unordered: `{ }`                                                                                                          | `tree [big, tall]`                                   |
| **Quantities**             | Integer: `×n` or `noun:n`<br>Value + unit: `noun:[value unit]`                                                                              | `soldier×5 march`<br>`forecast:[5d] unreliable`      |
| **Comparatives**           | Use standard math ops: `<`, `>`, `<=`, `>=`, `==`                                                                                           | `price_A < price_B`                                  |
| **Questions**              | Begin line with `?`                                                                                                                         | `? storm weaken`                                     |
| **Conditionals**           | Python-style conditional logic                                                                                                              | `if flood risk_high: city warn!`                     |
| **Pronouns / anaphora**    | Avoid pronouns and aliases. Repeat noun or use synonym.                                                                                     | —                                                    |
| **Word choice**            | Use the shortest unambiguous term from any language. Keep logical connectors (`if`, `and`, `or`) in English.                               | `心 break`                                            |
| **Grouped expressions**    | Use `{ }` for multiple subjects<br>Use `[ ]` for multiple verbs or objects                                                                  | `{city, town} evacuate [people:[1e6], pets]`         |
                                              |

## Example

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

## Copy-and-Paste Specification To Use in Prompts
```
Sentence frame: S V O. One clause per line.
Time markers:
  • Present = default
  • Future: +3d, +2h30m (suffix after verb)
  • Exact past: -2025-06-28T14:00-05
  • Imperfect: verb~
Negation: prefix ! or ¬ to verb → `cat !eat fish`
Modality:
  • ? = possible
  • ! = required/certain
  • !! = urgent imperative
Relations/prepositions: use as verb phrase → `book locate shelf`
Attributes:
  • Ordered: [ ]
  • Unordered: { }
Quantities:
  • Integer: ×n or noun:n
  • Value + unit: noun:[value unit]
Comparatives: <, >, <=, >=, ==
Questions: prefix ? to line
Conditionals: Python style → `if flood risk_high: city warn!`
Pronouns: avoid. Repeat noun or use synonym.
Word choice: use shortest unambiguous term from any language. Keep `if`, `and`, `or` in English.
Grouped expressions:
  • Multiple subjects: {city, town}
  • Multiple verbs or verb-objects: [people:[1e6], pets]
```

## How to Use It

### 1. **Manually**

Write compressed knowledge yourself using the spec above. One line = one fact or rule.

### 2. **With an LLM**

While LLMs can learn the syntax through examples alone get the best results by giving it the specification. 

Frontier models models like GPT-4o, Gemini 2.5 Falsh, and DeepSeek R1 can:

* Parse this DSL
* Unpack it into natural language
* Perform reasoning with the encoded data

## Contributing

Have a variant? Suggest a syntax tweak? Found a case where a model fumbles?

**Open an issue or submit a pull request.**
The more eyes on the grammar, the sharper it gets.

## License

[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) — free to use, remix, and extend with attribution. No commercial or proprietary forks.

---

## Questions?

Ping the creator. Or better yet—try it, break it, and post what you learn.

> "tree cast shade"
> — A system prompt, compressed.

## Citation

If you use Fact-RAR in your project, publication, or tool, please cite it as:

> Catarino David Delgado. *Fact-RAR: A Domain-Specific Language for Compressed Knowledge Representation in LLMs.* v0.1, 2025. [https://github.com/sidewaysthought/fact-rar](https://github.com/sidewaysthought/fact-rar)

BibTeX (optional):

```bibtex
@misc{factrar2025,
  author = {Catarino David Delgado},
  title = {Fact-RAR: A Domain-Specific Language for Compressed Knowledge Representation in LLMs},
  year = {2025},
  version = {0.1},
  url = {https://github.com/sidewaysthought/fact-rar}
}
