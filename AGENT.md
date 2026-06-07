# HalluJudge FSE '26 — Presentation

Interactive HTML slide deck for our FSE Companion '26 paper.
Paper source of truth: https://arxiv.org/html/2601.19072 (always fetch, no PDF in repo)

## Structure

```
slides/index.html          # single-file presentation (self-contained)
skills/paper-to-html-slides/SKILL.md  # slide generation skill
```

## Commands

```bash
open slides/index.html     # preview in browser
```

## Rules

- `slides/index.html` is always a single self-contained file — no build step, no bundler
- Never commit PDFs, binary assets, or API keys
- Always re-fetch the paper before updating slide content
- Read `skills/paper-to-html-slides/SKILL.md` before generating or editing slides
