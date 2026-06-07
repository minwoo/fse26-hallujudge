# HalluJudge — FSE '26 Presentation

Interactive HTML presentation for:

> **HalluJudge: A Reference-Free Hallucination Detection for Context Misalignment in Code Review Automation**
> FSE '26 (Industry track) · July 5–9, 2026 · Montreal, QC, Canada
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

This project uses Agents like [Claude Code](https://claude.ai/code), [Codex](https://chatgpt.com/codex), or [Rovo Dev](https://www.atlassian.com/software/rovo-dev) with the skill defined in `skills/paper-to-html-slides/SKILL.md`.

```bash
# Regenerate slides from paper
claude "Using AGENT.md and the skill in skills/paper-to-html-slides/SKILL.md, regenerate slides/index.html from the paper at https://arxiv.org/abs/2601.19072"

# Update a specific section
claude "Update the RQ1 results slide in slides/index.html with the latest numbers from the paper"
```

## Authors

Kla Tantithamthavorn (Monash University) · Hong Yi Lin (University of Melbourne) · Patanamon Thongtanunam (University of Melbourne) · Wachiraphan Charoenwet (University of Melbourne) · Minwoo Jeong (Atlassian) · Ming Wu (Atlassian)
