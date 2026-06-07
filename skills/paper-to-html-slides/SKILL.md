---
name: paper-to-html-slides
description: Convert an academic paper into an interactive HTML presentation. Use when asked to generate, update, or rebuild slides from a research paper.
---

# Skill: Paper → Interactive HTML Slides

Convert an academic paper into a self-contained single-file HTML presentation for conference delivery.

---

## Setup

Before starting, read `AGENTS.md` for project-specific context (paper URL, venue, authors, key results).

---

## Steps

### 1. Fetch the paper

Fetch the arXiv HTML version (`https://arxiv.org/html/<id>`) — not the PDF.

Extract: title, authors, venue, abstract, problem, approach, RQs, results (tables/figures), conclusion.

### 2. Plan the slide structure

Target **15–18 slides** for a 15–20 min talk. Typical arc:

> Title → Motivation → Problem → Approach → Study Design → RQ Results (one per RQ) → Discussion → Implications → Conclusion → Q&A

Adapt structure to the paper — don't force the template.

### 3. Build `slides/index.html`

Single self-contained file. No build step, no bundler.

**Theme (dark academic):**
```css
:root {
  --bg: #0f1117; --surface: #1a1d27; --border: #2e3350;
  --accent: #4f8ef7; --accent-ok: #34d399; --accent-warn: #f59e0b;
  --text: #e2e8f0; --text-muted: #8892a4;
  --font-head: 'DM Serif Display', Georgia, serif;
  --font-body: 'IBM Plex Sans', sans-serif;
  --font-mono: 'JetBrains Mono', monospace;
}
```
Fonts via Google Fonts CDN. No hardcoded colors outside `:root`.

**Typography:** Use `pt` units for font sizes — predictable on fixed-size slides (like PowerPoint/Keynote). Base body text at `16pt` intentionally small to handle content-heavy slides; scale up on sparse slides with utility classes:
```css
.text-lg { font-size: 20pt; } .text-xl { font-size: 24pt; } .text-2xl { font-size: 30pt; }
```
Slide-specific layout (grid, flex) goes inline. Repeated visual patterns (result boxes, callouts) get a CSS class.

**Layout:** 1200×675px (16:9), CSS `transform: scale()` for fullscreen. Max 5–6 bullets per slide.

**Navigation (required):**
```javascript
const slides = document.querySelectorAll('.slide');
let cur = 0;
function goTo(n) {
  slides[cur].classList.remove('active');
  cur = Math.max(0, Math.min(n, slides.length - 1));
  slides[cur].classList.add('active');
}
document.addEventListener('keydown', e => {
  if (['ArrowRight','Space'].includes(e.key)) { e.preventDefault(); goTo(cur+1); }
  if (['ArrowLeft','Backspace'].includes(e.key)) { e.preventDefault(); goTo(cur-1); }
  if (e.key === 'f') document.documentElement.requestFullscreen?.();
});
document.addEventListener('click', e => { if (!e.target.closest('.interactive')) goTo(cur+1); });
goTo(0);
```

**Slide transitions:**
```css
.slide { position: absolute; inset: 0; opacity: 0; transform: translateY(16px);
         transition: opacity 0.3s ease, transform 0.3s ease; pointer-events: none; }
.slide.active { opacity: 1; transform: translateY(0); pointer-events: all; }
```

**Result boxes:**
```css
.result-box { border-left: 3px solid var(--accent); background: rgba(79,142,247,0.08);
              padding: 0.75rem 1rem; border-radius: 0 8px 8px 0; }
.result-box.best { border-color: var(--accent-ok); background: rgba(52,211,153,0.08); }
```

### 4. Interactive elements

Add where it aids understanding — don't over-engineer:

- **Expandable panels** — for multi-part comparisons (e.g., comparing approaches). Use `class="interactive"` to prevent accidental slide advance.
- **Inline SVG charts** — for result tables with clear winners. Animate bars on slide entry with CSS `scaleY`.
- **Step reveal** — for walkthrough examples. Fade in content on click using `animation-delay`.

### 5. Verify before committing

- All numbers match the paper exactly
- No placeholder text (`TODO`, `[INSERT]`, `…`)
- Keyboard navigation works (`→`, `←`, `Space`, `f`)
- arXiv link present on title slide
