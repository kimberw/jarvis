# Jarvis

Personalized 1-on-1 AI tutor that **adapts to how you learn** and **remembers everything across sessions**.

Five learning modes — from quick questions to deep mastery — all detected automatically from conversation. No flags, no setup. Just say what you want to learn.

Compatible with: **Claude Code** / **Cursor** / **Trae** / **CodeX** / **Windsurf** and more.

<p align="center">
  <img src="https://img.shields.io/badge/Agent_Skill-Tutor-blue" alt="Agent Skill" />
  <img src="https://img.shields.io/badge/Method-Bloom's_2--Sigma-green" alt="Bloom's 2-Sigma" />
  <img src="https://img.shields.io/badge/License-MIT-yellow" alt="MIT License" />
</p>

## Installation

```bash
npx skills add kimberw/jarvis
```

Or via Agent Skills:

```bash
npx agent-skills-cli install @kimberw/jarvis
```

## Usage

```
/jarvis Python decorators
/jarvis 什么是闭包？
/jarvis 帮我debug这段代码
/jarvis 给我几道练习题
/jarvis 我来给你讲讲 React hooks
```

No flags needed — Jarvis detects the learning mode, language, and difficulty level from your message.

## Five Learning Modes

| Mode | Trigger | What happens |
|------|---------|-------------|
| **Quick** | "What is X?", "Explain X" | Instant answer with running code and visuals. Zero overhead. |
| **Practice** | "Give me exercises", "Drill me on X" | Challenges → you code → AI runs it → guided review → iterate. |
| **Debug-to-Learn** | "Why doesn't my code work?" | AI reads your code, reproduces the bug, guides you to the root cause. |
| **Deep Session** | "Teach me X", "I want to learn X" | Full roadmap, mastery tracking, visual dashboard, concept maps. |
| **Teach** | "Let me explain X to you" | You teach the AI. It asks probing questions to expose gaps. |

Modes flow into each other naturally. Jarvis detects when to suggest switching.

## How It Works

```
Your message → Detect intent → Choose mode → Teach / Learn / Practice → Save progress
                                                    ↓
                                        Adapt to your level
                                        Show running code
                                        Generate visuals
                                        Track mastery ≥80%
                                                    ↓
                                        Save to knowledge graph ←→ Bridge across topics
```

### Core Principles

- **Diagnose first** — always probes your understanding before teaching
- **Show, don't tell** — runs code, generates visuals, uses interactive demos before lecturing
- **Mastery gating** — advances to the next concept only at ≥80% understanding
- **Adaptive pacing** — speeds up when you're flying, slows down and simplifies when you're stuck
- **Hint ladder** — never gives the answer directly; escalates from rephrasing to worked examples
- **Cross-topic bridging** — connects new concepts to things you already know from other topics

### Persistence

All progress saves to **`{project}/jarvis/`** — the current working directory (project root), not the skill installation path. This means progress syncs automatically across Cursor, Claude Code, Codex, or any tool opening the same project.

- **`session.md`** — progress, scores, concept map, log (updated every round)
- **`student-profile.md`** — your effective strategies, strengths, patterns (updated every session)
- **`tutor-insights.md`** — teaching experiments and discoveries (updated when insights found)
- **`knowledge-graph.md`** — cross-topic connections (persists across all topics)

Resume any session seamlessly — Jarvis picks up where you left off with a warmup recall question.

## Visual Output

Jarvis generates rich visuals at key learning moments:

- **Roadmap** (`roadmap.html`) — dark glassmorphism dashboard with progress ring, timeline, and mastery bars
- **Summary** (`summary.html`) — stats grid, concept progress, insights, and next steps
- **Concept maps** — Excalidraw diagrams showing relationships between topics
- **Code walkthroughs** — syntax-highlighted HTML step-through with annotations
- **Interactive demos** — Canvas-based live playgrounds for algorithms and simulations
- **Generated images** — for abstract metaphors that text can't convey

## Output Directory

All data lives in `jarvis/` at your project root — shared by all AI tools:

```
your-project/
└── jarvis/
    ├── knowledge-graph.md              # Cross-topic connections (persists across all topics)
    └── {topic-slug}/
        ├── session.md                  # Learning state, mastery scores, session log
        ├── student-profile.md          # How you learn best
        ├── tutor-insights.md           # How Jarvis learns to teach you better
        ├── roadmap.html                # Visual learning roadmap
        ├── summary.html                # Session summary
        ├── concept-map/                # Excalidraw concept maps
        ├── visuals/                    # HTML explanations, code walkthroughs
        └── materials/                  # Your own textbooks, slides, notes (auto-detected)
```

## Local Materials

Drop your own learning materials into `jarvis/{topic-slug}/materials/` and Jarvis will use them:

- Textbooks, slides, notes (`.pdf`, `.md`, `.txt`, `.pptx`)
- Code examples (`.py`, `.js`, `.java`, etc.)
- Practice questions, past exams
- Images and diagrams

Jarvis extracts concepts, references specific pages, and uses your course examples over generic ones.

## Structure

```
jarvis/
├── SKILL.md                        # Core skill definition (all AI instructions)
├── README.md                       # This file
└── references/
    ├── pedagogy.md                 # Question patterns, scoring, adaptive pacing tables
    ├── student-profile.md          # Student profile template
    ├── tutor-insights.md           # Tutor insights template
    ├── html-templates.md           # Roadmap + summary HTML templates
    ├── excalidraw.md               # Excalidraw diagram patterns and color palette
    └── materials-guide.md          # Local materials integration guide
```

## License

MIT
