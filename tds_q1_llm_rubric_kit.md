# TDS Q1 — LLM Verification Rubric Kit (Generate → Stress-test → Rectify)

Unlike Q4, this one doesn't need a live exam-time variable — there's no topic or dataset to wait for. You can fully build and test this before the exam starts. A ready-to-use starter rubric is below so you're not starting blank; the three prompts let you regenerate, stress-test, or fix it live if needed.

---

## Starter rubric — ready to use as your answer, or refine further

This is itself the "prompt/evaluation rubric" the question asks for. Paste any article into it and hand it to any LLM.

```
You are a careful text-forensics analyst. Assess whether the article below shows common signs of AI-generated writing ("LLM smells"), consistently regardless of which language model is doing the assessment.

ARTICLE TO EVALUATE
[PASTE ARTICLE HERE]

SCORE EACH DIMENSION 0-3 (0 = no signs, 1 = mild, 2 = moderate, 3 = strong). For every score above 0, quote or point to the specific example that justifies it.

1. Filler & hedge language — overused transitions/hedges ("moreover," "furthermore," "it's important to note," "delve," "underscore," "navigate," "resonate," "utilize"), vague abstract words used as padding ("quietly," "shift," "hold," "pull," "signal," "the work"), or fake-candor openers ("Here's the kicker," "Honestly?", "But here's the thing").
2. Structural uniformity — paragraphs of near-identical length and energy throughout, with no variation in pacing; overused rule-of-three lists; the "It's not about X, it's about Y" contrast-reframe used as a false-insight device.
3. Vacuous/unfalsifiable claims — true-but-empty statements nobody could disagree with, that convey no specific information ("consistency matters," "success takes hard work").
4. Excessive both-sides framing — refuses to commit to a position; every claim gets immediately hedged or balanced.
5. Missing concrete specifics — no named people, dates, numbers, direct quotes, or lived/first-person detail; examples stay generic ("a company," "an expert") instead of named and checkable.
6. Suspicious precision — content lands exactly on a round word/section count, or shows unnatural symmetry between sections.
7. Generic open/close — opens with broad throat-clearing ("In today's world..."); closes by restating the intro instead of adding a final turn.
8. Punctuation/formatting tics — heavy em-dash use, excessive bolding, frequent three-item phrase lists within single sentences.

RULES FOR SCORING
- Score on PATTERN and FREQUENCY, not a single instance — one em dash or one "moreover" is normal human writing, not a signal.
- Before finalizing any dimension's score, ask: "could a skilled human writer have done this deliberately, for effect?" If yes, lower the score. Distinctive human style should not be penalized.
- Weight dimensions 1, 2, and 5 most heavily — hardest to fake convincingly. Weight 6, 7, and 8 lightest — easiest for a human editor to strip out of AI text.

OUTPUT FORMAT
1. A table: dimension | score (0-3) | one-line evidence
2. Total score (out of 24), noting whether the heavily-weighted dimensions (1, 2, 5) are driving the total
3. Verdict band: 0-6 = "likely human," 7-13 = "mixed / inconclusive," 14-24 = "likely AI-generated or heavily AI-assisted"
4. One line: confidence (low/medium/high) and why
5. One line disclaimer: this is a probabilistic stylistic signal, not proof of authorship
```

---

## Prompt 1 — Generate / customize the rubric

Use this if you want to regenerate the rubric live, or adapt it to slightly different exam wording.

```
You are an expert in computational linguistics and AI-text forensics. Design a scoring rubric that can be used to judge whether ANY given article shows common signs of AI-generated writing ("LLM smells").

REQUIREMENTS FOR THE RUBRIC
- Model-agnostic: works as a standalone prompt for any LLM (GPT, Claude, Gemini, etc.) — no model-specific references.
- Reusable: works on any article pasted in, not tuned to one specific piece of text.
- Structured as concrete, checkable dimensions, not vague adjectives like "sounds robotic."
- A numeric scale per dimension (e.g. 0-3), plus a rule for combining scores into an overall verdict with a stated confidence level.
- An explicit safeguard against false positives: a rule for when a pattern might be deliberate, distinctive human style rather than an AI tell.
- Dimensions weighted by how hard they are to remove or fake, not treated equally.
- Every non-zero score must require cited evidence (a quote or example), so the verdict is auditable, not just asserted.

OUTPUT
Produce the complete rubric as a ready-to-use prompt: a full instruction block that, when an article is pasted in and given to any LLM, returns a structured verdict. Output the rubric itself, ready to copy and reuse — no commentary about it.
```

---

## Prompt 2 — Stress-test the rubric

```
You will stress-test a detection rubric using the article below. Apply the rubric exactly as written, then answer the meta-questions beneath it.

RUBRIC
[PASTE YOUR RUBRIC HERE]

ARTICLE
[PASTE A SAMPLE ARTICLE — ideally one you know is human-written, and separately one you know is AI-written, tested one at a time]

APPLY THE RUBRIC, then answer:
1. Did the rubric produce the verdict you'd expect, given what you actually know about this article's origin?
2. Which dimension, if any, scored wrong — a false positive on genuine human style, or a miss on a real AI tell?
3. Was every non-zero score backed by a real quote/example, or asserted without evidence?
4. Rate the rubric's own writing 1-5: does the rubric prompt itself sound generic/AI-written? A rubric full of AI-sounding boilerplate undercuts its own credibility.
```

**Tip:** you have a guaranteed AI-written test sample sitting right there — run this against whatever essay your Q4 pipeline produces. And for a human-written sample, an old personal email or a pre-2020 published article works well since it predates LLM-influenced prose entirely.

---

## Prompt 3 — Rectify the rubric

```
Revise the rubric below to fix the issues found during testing, without losing its reusability or model-agnostic design.

CURRENT RUBRIC
[PASTE RUBRIC]

ISSUES FOUND (from stress-testing)
[PASTE ANSWERS FROM THE STRESS-TEST PROMPT]

INSTRUCTIONS
- Fix false positives by tightening the dimension's wording (add a "deliberate human style" exception) rather than deleting the dimension outright.
- Fix false negatives by adding or sharpening a dimension, not by lowering the verdict thresholds.
- Keep the rubric fully self-contained and copy-pasteable — no reference to this conversation or to any specific test article.
- Re-verify: every non-zero score still requires cited evidence.

OUTPUT
Return ONLY the revised rubric prompt, ready to copy and reuse.
```

---

## Before the exam

- Run the starter rubric against two samples now: one you know is human-written, one you know is AI-written (your Q4 essay output works perfectly). Confirm the verdict bands land where they should.
- If the real exam hands you an article to test live, you don't rebuild anything — just paste it into the starter rubric's `[PASTE ARTICLE HERE]` slot.
- Since "model-agnostic" is graded, if you have access to more than one LLM, running the same rubric + article through two of them and showing matching verdicts is a fast, visible way to demonstrate that requirement if asked.
