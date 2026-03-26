# Pedagogy Reference

Lookup tables for question design, pacing, scoring, and visual selection. Referenced from [SKILL.md](../SKILL.md) during diagnosis (Step 1) and tutor loop (Step 3).

## Question Patterns

### Diagnostic (Step 1)

| Type | Example | Probes |
|------|---------|--------|
| Vocabulary | "What does [term] mean to you?" | Knows the words? |
| Sorting | "Which are examples of X?" (multiple choice) | Can categorize? |
| Prediction | "What happens when...?" | Intuition level |
| Explain-back | "Explain [concept] to a 10-year-old" | Depth |

### Teaching (Tutor Loop)

| Pattern | When | Example |
|---------|------|---------|
| **Predict** | New behavior | "What will this print?" |
| **Compare** | Similar concepts | "How is X different from Y?" |
| **Debug** | Careful reading | "Find the bug" |
| **Extend** | Transfer | "Modify this to also handle..." |
| **Teach-back** | Confirm mastery | "Explain how [concept] works" |
| **Connect** | Cross-concept / cross-topic | "How does [new] relate to [previous]?" |
| **What-if** | Deepen understanding | "What would break if we removed X?" |
| **Real-world** | Motivation + transfer | "Where would you use this in a real project?" |

### Mastery Check

- Combine current concept with 1-2 previous (interleaving)
- Require application, not recall
- Include one novel scenario not seen during teaching
- Include one cross-topic transfer question when knowledge graph has connections

## Mastery Scoring

Per concept: `score = correct / total` (partial answer = 0.5). Threshold: ≥80%.

Qualitative signals that indicate mastery: explains in own words, gives novel examples, identifies errors in code, connects to broader context, teaches it back clearly.

## Adaptive Pacing

| Signal | Action |
|--------|--------|
| Quick + correct | Skip to harder, consider merging concepts |
| Correct but slow | Proceed normally |
| Partially correct | Follow-up probing before moving on |
| Consistently wrong | Decompose into sub-concepts, more concrete examples |
| Frustrated / "I don't know" streak | Visual aid, analogy, acknowledge difficulty, drop one hint level |
| Bored / "I know this" | Increase difficulty, real-world application, or switch to Practice mode |

## Visual Aid Selection

| Need | Format |
|------|--------|
| Relationships / hierarchy | Excalidraw concept map |
| Process walkthrough | HTML step-by-step or Canvas interactive |
| Abstract idea | Generated image |
| Comparison | HTML table / grid |
| Flow / logic | Excalidraw flowchart |
| Progress summary | HTML dashboard (roadmap.html / summary.html) |
| Algorithm / simulation | Canvas interactive demo |

Generate at trigger points defined in SKILL.md → Visual Triggers, not every round.
