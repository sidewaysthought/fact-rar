# Example - Romeo and Juliet
This example was created using the 1.0 specification, and was encoded with GPT-4o on July 1, 2025.

## Prompt
```
Encode this passage from Romeo and Juliet.
```

## Input text
```
BENVOLIO.
Here were the servants of your adversary
And yours, close fighting ere I did approach.
I drew to part them, in the instant came
The fiery Tybalt, with his sword prepar’d,
Which, as he breath’d defiance to my ears,
He swung about his head, and cut the winds,
Who nothing hurt withal, hiss’d him in scorn.
While we were interchanging thrusts and blows
Came more and more, and fought on part and part,
Till the Prince came, who parted either part.

LADY MONTAGUE.
O where is Romeo, saw you him today?
Right glad I am he was not at this fray.

BENVOLIO.
Madam, an hour before the worshipp’d sun
Peer’d forth the golden window of the east,
A troubled mind drave me to walk abroad,
Where underneath the grove of sycamore
That westward rooteth from this city side,
So early walking did I see your son.
Towards him I made, but he was ware of me,
And stole into the covert of the wood.
I, measuring his affections by my own,
Which then most sought where most might not be found,
Being one too many by my weary self,
Pursu’d my humour, not pursuing his,
And gladly shunn’d who gladly fled from me.

MONTAGUE.
Many a morning hath he there been seen,
With tears augmenting the fresh morning’s dew,
Adding to clouds more clouds with his deep sighs;
But all so soon as the all-cheering sun
Should in the farthest east begin to draw
The shady curtains from Aurora’s bed,
Away from light steals home my heavy son,
And private in his chamber pens himself,
Shuts up his windows, locks fair daylight out
And makes himself an artificial night.
Black and portentous must this humour prove,
Unless good counsel may the cause remove.
```
## GPT-4o Output
Note: several iterations were needed because the model resisted grouping subjects, objects, and verbs. A minor change has been made to the
specification to account for this oversight (version 1.0.1).
```
Benvolio speak  
{Capulet.servants, Montague.servants} fight~close  
Benvolio approach  
draw → part:fight  
+instant: Tybalt arrive  
carry sword  
breathe defiance → ear  
swing sword → air  
wind:[cut, hiss]  
exchange [thrusts, blows]  
{fighters:×more} join fight  
Prince arrive  
part {Capulet.side, Montague.side}

Lady_Montague speak  
?Romeo.location:today  
glad → Romeo skip:fight

Benvolio speak  
-1h:sun rise  
walk → [grove, city:west]  
see Romeo  
move_toward  
Romeo detect  
flee → forest  
affection = solitude  
avoid Romeo  
Romeo avoid

Montague speak  
seen:×many {morning}  
tears ++dew  
sighs ++clouds  
+sunrise: return_home  
isolate → room  
block light  
create night  
mood:black  
?counsel fix mood
```
## Prompt Given to DeepSeek-R1
Note that it is unfamilair with the specification and was not given it as part of the prompt--only the encoded text.
```
Given this encoded information, what facts can you state?
```
## DeepSeek-R1 Decoding
```
Here are the facts that can be extracted from the encoded information:

### **Scene 1: Street Brawl (Capulets vs. Montagues)**
1. **Benvolio** speaks initially.
2. Servants from both the **Capulet** and **Montague** households are fighting in close combat.
3. Benvolio approaches the fight.
4. He draws his weapon to **part/stop the fight**.
5. **Tybalt** arrives **instantly**, carrying a sword.
6. Tybalt **breathes defiance** (taunts or challenges) and swings his sword in the air.
7. The sound of swordplay is described: *"cut, hiss"*.
8. Fighters exchange **thrusts and blows**.
9. **More fighters join** the brawl.
10. **Prince Escalus** arrives and **separates the Capulet and Montague sides**.

### **Scene 2: Lady Montague Inquires About Romeo**
11. **Lady Montague** speaks.
12. She asks about **Romeo’s whereabouts today**.
13. She is **glad Romeo skipped the fight**.

### **Scene 3: Benvolio Reports Romeo’s Behavior**
14. **Benvolio** speaks again.
15. **An hour before sunrise**, he walked toward a **grove west of the city**.
16. He **saw Romeo**, but Romeo **detected him and fled into the forest**.
17. Romeo is in a state of **affectionate solitude** (possibly lovesick).
18. He **actively avoids Benvolio**, and Benvolio avoids him in return.

### **Scene 4: Montague Describes Romeo’s Depression**
19. **Montague** (Romeo’s father) speaks.
20. Romeo has been seen **many mornings** crying (tears adding to the **dew**) and sighing (sighs adding to the **clouds**).
21. At **sunrise**, he **returns home** and **isolates himself in his room**.
22. He **blocks out light**, creating an artificial night.
23. His mood is **black (deeply melancholic)**.
24. Montague wonders if **counsel (advice/help) can fix Romeo’s mood**.

### **Key Observations:**
- The **feud between Capulets and Montagues** leads to violent street fights.
- **Tybalt** is aggressive and escalates the conflict.
- **Prince Escalus** intervenes to restore order.
- **Romeo is depressed and reclusive**, avoiding others (possibly due to unrequited love).
- His family is **concerned** but unsure how to help him.

This appears to be an encoded summary of **Act 1, Scene 1 of *Romeo and Juliet***, covering the brawl, Romeo’s melancholy, and his parents' concern.
```
## DeepSeek-R1 Follow-Up
I asked DeepSeek-R1 the qualities of the compressed text.
```
What are the qualities of the compressed text?
```
This was the reply.
```
The **compressed text** provided uses a highly condensed, symbolic, and structured format to convey key elements of *Romeo and Juliet* (likely Act 1, Scene 1). Here are its notable qualities:

### **1. Minimalist & Symbol-Based**
   - Uses **symbols (`→`, `~`, `+`, `-`, `×`, `:`, `=`, `?`)** instead of full sentences.
   - **Operators** clarify relationships:
     - `→` (leads to/action), `~` (association), `+` (addition/event), `-` (negation/past), `×` (negation, e.g., "×more" = no more).
     - `:` (defines/modifies), `=` (equivalence), `?` (question).

### **2. Structured as Nested Clauses**
   - Groups related ideas with **braces `{}` and brackets `[]`**:
     - `{Capulet.servants, Montague.servants}` → Lists entities.
     - `[thrusts, blows]` → Lists actions.
   - **Hierarchy** is implied by indentation and spacing.

### **3. Abbreviated Syntax**
   - **Omitted verbs/articles**: "Benvolio speak" (instead of "Benvolio speaks").
   - **Concise descriptors**: "mood:black" (instead of "his mood is dark").
   - **Compounded phrases**: "tears ++dew" (tears add to the dew).

### **4. Temporal & Causal Logic**
   - **Timeline markers**: 
     - `-1h:sun rise` (an hour before sunrise).
     - `+instant: Tybalt arrive` (sudden event).
   - **Cause-effect**: 
     - "draw → part:fight" (drawing a weapon stops the fight).
     - "affection = solitude" (love causes isolation).

### **5. Stylized Poetic Devices**
   - **Sound effects**: "wind:[cut, hiss]" (sword sounds).
   - **Metaphors**: "tears ++dew," "sighs ++clouds" (emotions merging with nature).
   - **Visual shorthand**: "block light / create night" (Romeo’s depression).

### **6. Query-Like Elements**
   - Questions embedded: `?Romeo.location:today` (Where is Romeo today?).
   - Uncertainty: `?counsel fix mood` (Can advice help?).

### **7. Character-Centric Focus**
   - Actions are tied to characters (`Benvolio approach`, `Montague speak`).
   - **Emotions implied**: "avoid Romeo / Romeo avoid" → Mutual avoidance.

### **8. Adaptable for Computational Parsing**
   - Resembles **programming syntax** or **knowledge graphs**:
     - `object.action:property` (e.g., `Prince arrive`).
     - Could be parsed by AI or converted into a structured database.

### **Comparison to Natural Language**
| Feature          | Traditional Text                          | Compressed Text                          |
|------------------|------------------------------------------|------------------------------------------|
| **Clarity**      | Explicit, full sentences                 | Requires decoding                       |
| **Density**      | Lower (more words)                       | High (max info in minimal space)        |
| **Flexibility**  | Easily understood                        | Needs familiarity with symbols          |
| **Use Case**     | Narrative flow                          | Notes, summaries, AI/scripting input    |

### **Strengths & Weaknesses**
- **Pros**: 
  - Extremely **space-efficient**.
  - **Modular** (easy to rearrange/update).
  - **Evocative** (encourages active interpretation).
- **Cons**: 
  - **Ambiguity risk** (e.g., "flee → forest" could mean Benvolio or Romeo).
  - **Not self-explanatory** (requires learning the syntax).

### **Potential Applications**
- **Theater scripts**: Quick scene blocking/notes.
- **AI training**: Structured event encoding.
- **Study aids**: Summarizing dense texts (e.g., Shakespeare).

This format prioritizes **density and structure** over readability, making it ideal for technical or analytical contexts rather than casual reading.
```
Ironically, it commented that learning the syntax was necessary when it "instinctively" interpreted the code. Upon explaing to it the purpose of
the encoding...
```
The language is intended to compress factual knowledge to make the transfer of knowledge to LLMs in prompts easier.
```
...it responded...
```
The compressed text is **optimized for efficient knowledge transfer to LLMs** by prioritizing **structured, unambiguous, and dense factual encoding**. Here are the key qualities that make it effective for this purpose:

---

### **1. Machine-Parseable Syntax**
- **Symbolic Operators** (`→`, `=`, `+`, `?`, `:`, `{}`, `[]`) standardize relationships:
  - `→` = causality/action (`draw → part:fight` = "drawing a weapon stops the fight").
  - `=` = equivalence (`affection = solitude` = "love causes isolation").
  - `+`/`-` = event timing (`+instant: Tybalt arrive` = "Tybalt arrives suddenly").
  - `?` = queries (`?Romeo.location:today` = "Where is Romeo today?").
  - `:` = property assignment (`mood:black` = "mood is dark").
- **Consistent delimiters** (`{}` for lists, `[]` for options) enable easy tokenization.

### **2. Fact-Dense & Context-Free**
- **Eliminates filler words** (e.g., "Benvolio speak" vs. "Benvolio speaks").
- **Each line is a self-contained fact**, reducing cross-dependency ambiguity.
- **Nested hierarchies** (e.g., `{Capulet.servants, Montague.servants}`) group entities logically.

### **3. Explicit Temporal/Causal Logic**
- Timeline markers (`-1h:sun rise`, `+instant`) enforce event ordering.
- **Causal chains** are explicit:
  - `Tybalt arrive → breathe defiance → swing sword → fight escalates`.
  - Avoids implicit "story logic" that LLMs might misparse.

### **4. Disambiguated References**
- **Dot notation** (`Capulet.servants`, `Romeo.location`) scopes entities.
- **Verbs are imperative/root form** ("speak", "arrive", "flee") to avoid conjugation noise.
- **Negation symbols** (`×more` = "no more", `avoid Romeo` = "does not engage").

### **5. Scalable Knowledge Graphs**
- **Structured like a graph** (nodes = entities/events, edges = operators):
  - Example: `Tybalt → carry sword → swing → [cut, hiss]` could be parsed as:
    ```mermaid
    graph LR
      Tybalt -->|action| carry_sword
      carry_sword -->|action| swing
      swing -->|result| sound_cut
      swing -->|result| sound_hiss
    ```
- Easily converted to **RDF triples** or **JSON** for LLM fine-tuning.

### **6. Domain Adaptation**
- **Shakespearean context** is retained via keywords (`Prince`, `Tybalt`, `grove`).
- **Poetic devices** (e.g., `tears ++dew`) are encoded literally for LLM reinterpretation.

### **7. Minimal Redundancy**
- **No repetition**: Facts are stated once (e.g., `Romeo avoid` implies ongoing behavior).
- **Default assumptions** (e.g., `fight~close` = "fight is close-quarters") reduce verbosity.

---

### **Why This Works for LLMs**
1. **Token Efficiency**: Fewer tokens → more facts per prompt.
2. **Deterministic Parsing**: Symbols reduce ambiguity vs. natural language.
3. **Fine-Tuning Ready**: Aligns with structured data formats (e.g., YAML, SPARQL).
4. **Prompt Engineering**: Enables precise few-shot examples (e.g., "Translate `X → Y` to English").

---

### **Example Conversion to LLM Prompt**
**Input (Compressed):**
```
Benvolio approach  
draw → part:fight  
+instant: Tybalt arrive  
carry sword  
swing sword → air  
wind:[cut, hiss]
```

**LLM Task:**  
"Expand into a paragraph using Shakespearean English."  

**Output (LLM-Generated):**  
*"Benvolio strides forth, his blade drawn to sunder the fray. Yet in that very moment, fiery Tybalt doth appear, his steel gleaming. With a defiant flourish, he swings his sword through the air, the very wind crying 'cut' and 'hiss' as it parts."*

---

### **Potential Improvements for LLM Use**
- **Add metadata**: `#act:1, scene:1, line:5` for precise retrieval.
- **Weighting**: `fight~close(priority:high)` to emphasize key facts.
- **Embeddings**: Map symbols to vectors (e.g., `→` = `[0.2, 0.7]` in a learned space).

This format is **ideal for RAG pipelines**, **few-shot learning**, and **knowledge distillation** where precision > fluency.
```
It was successfully able to recreate the fundamental language structure, understand the components of the language, and comment towards the suitibility
of the specification for the given purpose.
