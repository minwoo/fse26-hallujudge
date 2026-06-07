# HalluJudge — FSE '26 Presentation

Interactive HTML presentation for:

> **HalluJudge: A Reference-Free Hallucination Detection for Context Misalignment in Code Review Automation**
> FSE Companion '26 · July 5–9, 2026 · Montreal, QC, Canada
> [arXiv:2601.19072](https://arxiv.org/abs/2601.19072)

## Quick Start

```bash
# Clone the repo
git clone <repo-url>

# Open presentation in browser (no build step needed)
open slides/index.html
```

## Navigation

| Key | Action |
|-----|--------|
| `→` / `Space` / Click | Next slide |
| `←` / `Backspace` | Previous slide |
| `f` | Toggle fullscreen |

## Updating the Slides

This project uses [Claude Code](https://claude.ai/code) with the skill defined in `skills/paper-to-html-slides/SKILL.md`.

```bash
# Regenerate slides from paper
claude "Using CLAUDE.md and the skill in skills/paper-to-html-slides/SKILL.md, regenerate slides/index.html from the paper at https://arxiv.org/abs/2601.19072"

# Update a specific section
claude "Update the RQ1 results slide in slides/index.html with the latest numbers from the paper"
```

## Authors

Kla Tantithamthavorn (Monash) · Hong Yi Lin (Melbourne) · Patanamon Thongtanunam (Melbourne) · Wachiraphan Charoenwet (Melbourne) · **Minwoo Jeong (Atlassian)** · Ming Wu (Atlassian)
