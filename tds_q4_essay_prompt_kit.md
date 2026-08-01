# TDS Q4 — Essay Prompt Kit (Generate → Evaluate → Revise)

The moment the topic drops, paste Prompt 1. Feed its output into Prompt 2. Feed that into Prompt 3. Every prompt below is copy-paste ready — just fill in the bracketed placeholders.

---

## Prompt 1 — Generate

```
You are a sharp, original essayist known for concise, memorable prose with a distinct point of view — the opposite of generic AI-generated writing.

TASK
Write a short essay on the topic below.

TOPIC
[INSERT TOPIC HERE]

BEFORE WRITING (do this silently — don't show it in your output)
Consider at least 3 different angles on this topic, including ones most people would NOT immediately reach for. Pick the angle that is most specific and least obvious, and commit to it fully.

REQUIREMENTS
- Maximum 150 words. Aim for 140-148 — don't pad to hit the ceiling, and don't stop well short of it either.
- Take ONE clear, defensible position. No "on one hand / on the other hand" balancing.
- Open with a concrete claim, image, or example — never "In today's world..." or "X has become increasingly important..."
- Develop the claim with one specific example, comparison, or piece of reasoning — not a list of three generic points.
- Close with a line that sharpens or complicates the opening claim — not a summary ("In conclusion...").
- Every sentence must clearly serve the stated topic — no drifting into tangential themes.
- Vary sentence length and rhythm; avoid uniform sentence structures.

AVOID (these read as generic AI writing)
- Filler/hedge phrases: "it is important to note," "in today's fast-paced world," "moreover," "furthermore," "in conclusion"
- Triplet lists used as a structural crutch
- Perfectly balanced both-sides framing
- Abstract nouns used as padding ("innovation," "synergy," "landscape") without something concrete behind them
- Restating the topic/prompt in your opening sentence

OUTPUT
Return ONLY the essay text. No title, no word count, no preamble, no notes.
```

---

## Prompt 2 — Evaluate

```
You are a strict exam evaluator grading for a comparative exam, where originality and distinctiveness count as much as correctness.

TASK
Evaluate the essay below and output structured feedback. Do not rewrite it yet.

TOPIC
[INSERT SAME TOPIC HERE]

ESSAY TO EVALUATE
[PASTE ESSAY HERE]

SCORE EACH 1-5, WITH A ONE-LINE JUSTIFICATION
1. Topic relevance — does every sentence directly serve the stated topic?
2. Originality — is this angle distinctive, or the first/obvious thing most people would write? (Score low if obvious.)
3. Human voice — any signs of generic AI writing: hedging, filler transitions, listy triplets, both-sides framing, abstract-noun padding?
4. Argument strength — one clear, well-supported claim, or vague/scattered?
5. Word count — state the exact count; flag if over 150.

THEN OUTPUT
- "Biggest weakness": one sentence naming the single thing most limiting this essay's score.
- 2-3 concrete, actionable revision instructions — not "make it better," specific edits (e.g. "cut sentence 2, it restates the topic instead of adding a claim").
```

**Tip:** if your Question 1 rubric ends up naming specific "LLM smells," paste those markers into dimension 3 here — reuse your own rubric to grade your own essay.

---

## Prompt 3 — Revise

```
You are the same essayist from before. Revise the essay using the evaluation feedback, without breaking the original constraints.

TOPIC
[INSERT TOPIC]

ORIGINAL ESSAY
[PASTE ESSAY]

EVALUATION FEEDBACK
[PASTE OUTPUT FROM THE EVALUATION PROMPT]

INSTRUCTIONS
- Fix the "biggest weakness" and apply the revision instructions directly.
- Stay under 150 words (aim 140-148).
- If originality was marked weak, don't hedge or soften the claim to compensate — sharpen it further.
- Keep what already works; don't rewrite sentences that weren't flagged.
- Recheck: every sentence must serve the stated topic.

OUTPUT
Return ONLY the revised essay. No notes, no explanation, no word count.
```

---

## Fast-path — if the clock's tight

Merges evaluate + revise into a single call. Use this if you don't have time for all three steps separately.

```
You are a sharp, original essayist and a strict exam evaluator in one.

STEP 1 (silent): Evaluate the essay below on topic relevance (every sentence serves the topic), originality (not the obvious/generic angle), human voice (no hedging, filler transitions, listy triplets, both-sides framing), argument strength (one clear, supported claim), and word count (≤150).

STEP 2: Rewrite to fix the biggest weakness while keeping what works. Don't soften the claim to fix originality — sharpen it.

TOPIC
[INSERT TOPIC]

ESSAY
[PASTE ESSAY]

OUTPUT
Return ONLY the revised essay. No evaluation notes, no explanation, no word count.
```

---

## Worked example (placeholder topic — so you can see the pipeline work before the real one drops)

**Topic used:** "Should students be permitted to use AI tools during exams?"

**Prompt 1 output:**
> When calculators entered math classrooms, nobody worried students would forget how to add — they worried students would stop learning what addition was for. AI in exams raises the same question, wrongly answered by banning it. A student who can prompt a model into producing three verified, surprising insights from an unfamiliar dataset in ten minutes has demonstrated judgment a closed-book exam never touches: knowing which questions are worth asking, and which answers deserve suspicion. The real risk isn't that AI writes the sentence — it's that a grader still asks for the sentence, instead of asking why it should be believed. An exam that rewards verification over recall doesn't get weaker with AI in the room. It finally tests the right thing.

*(121 words)*

**Prompt 2 output (abridged):**
- Topic relevance: 5/5
- Originality: 4/5 — the calculator analogy is a real angle, not the default "cheating vs. fairness" framing
- Human voice: 5/5 — no hedging, no triplets, no throat-clearing opener
- Argument strength: 4/5 — the "real risk" sentence introduces a second claim instead of deepening the first
- Word count: 121/150
- Biggest weakness: mid-essay pivot dilutes focus by raising a second claim instead of extending the first one

**Prompt 3 output:**
> When calculators entered math classrooms, nobody worried students would forget how to add — they worried students would stop learning what addition was for. AI in exams raises the same question, wrongly answered by banning it. A student who can prompt a model into producing three verified, surprising insights from an unfamiliar dataset in ten minutes has demonstrated judgment a closed-book exam never touches: knowing which questions are worth asking, and which answers deserve suspicion — the same judgment a calculator never tested and a ban never taught. An exam built to reward that judgment doesn't get weaker with AI in the room. For the first time, it's testing the right thing.

*(112 words)*

---

## Before the exam

- Run Prompt 1 once now with any throwaway topic so you're not debugging prompt wording live.
- With 45 minutes across 4 questions, budget for one full generate → evaluate → revise pass on the essay, not several loops. Use the fast-path if time is tighter than expected.
