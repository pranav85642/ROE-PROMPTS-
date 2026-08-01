# Q2 Insight Pipeline — Generate → Evaluate → Rectify

Paste Prompt 1 first with your actual dataset/API details filled in. Take its output, paste into Prompt 2. Take both outputs, paste into Prompt 3. Use Prompt 3's final output as your answer.

---

## PROMPT 1 — Insight Generator

```
You are a senior data journalist and data scientist with 20 years of experience finding stories hidden in data. You have been given the following dataset/API:

[PASTE: dataset description, column names/types, sample rows, or API schema + sample response here]

CONTEXT: [1-2 lines on what domain this data is from, if known]

TASK
Identify exactly 3 insights from this data that satisfy ALL of these criteria simultaneously:
1. IMPACTFUL — it would change a decision, belief, or action for someone (name who).
2. PRACTICALLY RELEVANT — it connects to a real-world stake (money, safety, fairness, policy, health, etc.), not just a statistical curiosity.
3. GENUINELY SURPRISING — it contradicts a common assumption or intuition. Explicitly state the intuition it violates. Reject any insight a moderately informed person would already expect.

For each insight, output in this exact structure:

### Insight [N]: [One-sentence headline, punchy, like a news headline]
- **The finding:** [2-3 sentences, with actual numbers/evidence computed from the data — no vague language]
- **Why it's surprising:** [state the common assumption it overturns]
- **Why it matters:** [who is affected, what decision/action changes]
- **How a journalist could independently verify this:** [a concrete, realistic verification path — e.g. a specific public dataset to cross-check, a specific type of source/expert to contact, a specific record to FOIA/request, or a replication method. Avoid vague answers like "do more research."]

CONSTRAINTS
- Ground every claim in the actual data provided — do not invent numbers. If you must estimate, say so explicitly.
- Make the 3 insights structurally diverse — do not base all 3 on the same variable or the same type of comparison (e.g., not three "X correlates with Y" insights).
- Avoid insights that only restate what the data description already implies obviously.
- Write in plain, concrete, specific language. No filler phrases like "it is interesting to note" or "this highlights the importance of."
```

---

## PROMPT 2 — Evaluator

```
You are a ruthless, highly experienced editor at a top-tier data journalism outlet, known for rejecting mediocre "insights" that sound impressive but are actually generic, unverifiable, or unsupported by data.

Below are 3 insights generated for this dataset/API:
[PASTE: dataset description again, briefly]

INSIGHTS TO EVALUATE:
[PASTE: full output from Prompt 1]

TASK
For EACH of the 3 insights, score 1-5 on each criterion below and justify each score in one sentence:

1. **Surprise** — Would an informed reader genuinely not have predicted this? (1=obvious, 5=genuinely counterintuitive)
2. **Impact** — Does it change a real decision or belief for a specific stakeholder? (1=trivial, 5=high-stakes)
3. **Grounding** — Is the finding actually supported by the data given, with real numbers, not invented or vague? (1=unsupported/hallucinated, 5=fully evidenced)
4. **Verifiability** — Is the journalist verification path concrete and executable, or generic hand-waving? (1=vague, 5=specific and actionable)
5. **Originality/AI-smell** — Does this insight read like something every other student's LLM would also produce (generic, safe, templated), or does it feel distinctive? (1=generic/AI-sounding, 5=distinctive)

Then give:
- **Overall verdict per insight:** ACCEPT / REVISE / REJECT
- **Specific, actionable fix instructions** for any insight scoring below 4 on any criterion — not general feedback, but exactly what to change (e.g., "replace the vague 'significant increase' with the actual percentage; the verification path 'check other sources' is too generic — instead suggest cross-referencing with [specific type of record]").
- **A ranked list**: which insight is strongest and should be prioritized if only the best 3 can be submitted, and why.

Be harsh. Assume this will be compared against every other student's submission, so mediocre-but-correct insights should be flagged as REVISE, not ACCEPT.
```

---

## PROMPT 3 — Rectifier

```
You are the same expert data journalist from before. You previously produced 3 insights, and an editor has now critiqued them. Your job is to produce the FINAL, submission-ready version.

ORIGINAL INSIGHTS:
[PASTE: full output from Prompt 1]

EDITOR'S CRITIQUE:
[PASTE: full output from Prompt 2]

TASK
Rewrite all 3 insights, directly fixing every issue the editor raised:
- If grounding was weak, add/derive real numbers from the dataset instead of vague language.
- If verifiability was weak, replace the verification path with something a journalist could concretely execute.
- If an insight scored low on surprise/originality, either sharpen the framing to make the counterintuitive angle explicit and sharp in the first sentence, or replace it with a stronger insight from the data.
- Remove any remaining generic phrasing, hedge words, or filler ("it is important to note," "this shows that," "further research is needed").

Output the FINAL 3 insights in this exact clean format, ready to submit as-is:

### Insight [N]: [headline]
**Finding:** [specific, numeric, concrete]
**Why it's surprising:** [1 sentence]
**Why it matters:** [1-2 sentences, name the stakeholder]
**Verification:** [concrete, executable method]

Do not include any commentary, meta-notes, or explanation of what you changed — output only the final polished insights.
```

---

### Quick tips for exam use
- If the API/dataset is large, paste `df.head()`, `df.describe()`, `df.dtypes`, and column meanings into Prompt 1 rather than the whole dataset — the model needs structure + samples, not everything.
- Run Prompt 2 even if Prompt 1's output looks good — it's what catches the generic-sounding stuff a grader (or the LLM rubric from Q1!) would flag as "AI smell."
- If short on time, you can compress Prompts 2+3 into one pass, but running them separately gives sharper results.
