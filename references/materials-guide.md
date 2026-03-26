# Local Materials Guide

> Using local learning materials with Jarvis for personalized tutoring

## Quick Start

```bash
mkdir -p jarvis/{topic-slug}/materials
cp ~/Downloads/course-slides.pdf jarvis/{topic-slug}/materials/
/jarvis {topic}
```

Jarvis auto-detects materials and uses them throughout the session. You can also add files during a session.

## Supported File Types

| Category | Extensions | How Jarvis Uses It |
|----------|------------|-------------------|
| Documents | `.pdf`, `.md`, `.txt`, `.docx` | Extracts text, references specific pages/sections |
| Presentations | `.pptx`, `.ppt`, `.key` | Extracts slides, text, key concepts |
| Code | `.py`, `.js`, `.java`, etc. | Uses as examples, exercises, walkthroughs |
| Data | `.json`, `.csv`, `.yaml` | Datasets for practice, configuration examples |
| Images | `.png`, `.jpg`, `.svg`, `.gif` | Diagrams, charts, visual aids |

## How Jarvis Uses Materials

| Phase | Without Materials | With Materials |
|-------|-------------------|----------------|
| Roadmap | Generic topic decomposition | Concepts extracted from your syllabus |
| Explanations | General knowledge | References your textbook pages |
| Examples | Generic examples | Examples from your course materials |
| Practice | Generated questions | Questions from your practice sets |
| Diagrams | AI-generated visuals | Diagrams from your materials |

## Recommended Organization

```
materials/
├── core/               # Syllabus, main textbook — read first
├── slides/             # Lecture slides by module
├── practice/           # Exercises, quizzes, past exams
└── notes/              # Personal notes
```

Use descriptive filenames (`chapter-5-decorators.pdf`, not `1.pdf`). Optionally add a `README.md` describing each file's contents and priority.

## Material Processing Notes

- **PDFs**: Text extraction via Read tool; can reference specific pages. Password-protected or scanned PDFs may need OCR preprocessing.
- **Markdown/Text**: Read directly with full formatting preserved.
- **Code files**: Read, referenced as examples, can be executed for practice.
- **Images**: Displayed during tutoring, extracted from PDFs when relevant.

## Integration with Jarvis Features

Materials integrate with the full tutoring system:
- **Student profile**: Tracks which materials are most effective for you
- **Tutor insights**: Discovers patterns in material-based teaching
- **Visual roadmap**: Shows which materials cover which concepts
- **Top-down mode**: Uses materials to support project-based learning

## Privacy

All materials stay local. Files are never uploaded. Processing happens on your machine.
