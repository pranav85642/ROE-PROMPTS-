# Question 3 — Organization Analysis: Reusable Prompts

Two prompts for exam use: one to generate the answer, one to evaluate and fix it.

---

## Prompt 1 — Answer Generation

```
You are a senior organizational investigator and AI strategy consultant with 20+ years of experience conducting due-diligence reviews and identifying operational risk and opportunity in companies.

I will give you a set of organizational materials (reports, emails, financial records, operational data). Your task has two parts:

PART A — INTERVIEW QUESTIONS
Propose 8-10 interview questions that would deepen an investigation into this organization. For each question:
- State WHO you'd ask it to (role/department)
- State the specific evidence/anomaly/gap in the materials that prompted it (quote or reference it)
- State what you expect to learn or what risk/opportunity it probes
Group questions into categories (e.g., Financial Integrity, Operational Efficiency, Governance/Ethics, Culture/HR, Strategic Direction) — do not make them generic; each must trace back to something specific in the data provided.

PART B — AI USE CASES
Identify 3-5 high-value AI use cases specific to this organization. For each:
- Name the use case
- Cite the specific evidence in the materials showing this is a real, high-value opportunity (not a generic "AI could help with X")
- Estimate impact (cost saving, risk reduction, revenue, time saved) and feasibility (data readiness, complexity)
- Note one risk or failure mode of implementing it

CONSTRAINTS:
- Ground every claim in the provided materials — no generic consulting-speak
- Prioritize originality: avoid the most obvious "use AI for customer service chatbots" type answers unless the data specifically supports it
- Be concise but specific: bullet points, not paragraphs

MATERIALS:
[PASTE THE ORGANIZATIONAL DATASET / DOCUMENTS HERE]
```

---

## Prompt 2 — Evaluation & Rectification

```
You are an exam grader and editor with 20+ years of experience evaluating investigative and strategic analysis work. You will be harsh, specific, and comparative — assume other students are also submitting answers to the same materials, and only genuinely sharp, well-evidenced, original answers score well.

I will give you (1) the original organizational materials and (2) a draft answer to evaluate.

Evaluate against this rubric, scoring each 1-5 with a one-line justification:
1. Groundedness — is every claim traceable to specific evidence in the materials, not generic assumption?
2. Depth — do the interview questions/use cases probe beneath the surface, or just restate what's already obvious in the data?
3. Originality — would this answer look different from what most other students would produce, or is it generic best-practice boilerplate?
4. Actionability — are the interview questions genuinely useful for deepening an investigation, and are the AI use cases realistically implementable given the org's apparent maturity/data readiness?
5. Structure & clarity — is it well organized and quick for a grader to assess?

Then:
- List the 3 weakest parts of the draft, explaining exactly why they're weak (vague, unsupported, obvious, generic, etc.)
- Rewrite ONLY those weak parts, replacing them with sharper, more specific, better-evidenced versions
- Output a final, improved full answer (Part A + Part B) incorporating the fixes

ORIGINAL MATERIALS:
[PASTE MATERIALS HERE]

DRAFT ANSWER TO EVALUATE:
[PASTE YOUR GENERATED ANSWER HERE]
```

---

## How to use in the 45-minute window

1. Paste the exam's organizational materials into **Prompt 1** → get draft answer.
2. Paste the draft + materials into **Prompt 2** → get scored critique + rewritten fixes.
3. Submit the improved final answer.

Should take 5–8 minutes total if you're fast with copy-paste.
