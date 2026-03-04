# p135246.github.io — Pavel Hájek's Personal Website

## Overview

Jekyll-based personal website hosted on GitHub Pages. Contains blog posts on math, software, IT, and Wolfram-related topics.

## Site structure

- `_config.yml` — Jekyll configuration
- `_layouts/` — `post.html`, `page.html`, `category.html`
- `_includes/` — HTML snippets (mathjax, utterances comments)
- `_sass/` — CSS
- `assets/` — static files (PDFs, images)
- `_drafts/` — unpublished posts (excluded from git via .gitignore)
- `_site/` — generated output (excluded from git)

## Content categories (each is a top-level folder with `_posts/`)

- `IT/` — technical how-tos (e.g., screen sharing, website changelog)
- `Math/` — mathematical content (theses, IBL algebra, field tax)
- Top-level `.md` files: `Software.md`, `Wolfram.md`, `Math.md`, `Academia.md`, etc. — these are category landing pages

## Post format

Front matter:
```yaml
---
title:      "Post title"
categories: [Math, Wolfram]   # or single: Software
mathjax:    true               # enable LaTeX rendering
utterances: true               # enable comments
---
```

Posts go in `<Category>/_posts/YYYY-MM-DD-slug.md`.
Drafts go in `_drafts/` without date prefix.

## Writing style (Pavel's voice)

- Concise, first-person, matter-of-fact
- Technical but accessible — explains the "why" not just the "how"
- Uses Markdown link references at bottom of file: `[label]: url`
- Numbered lists for sequential steps, otherwise prose
- Light humor, no fluff
- Often includes "prerequisities", "steps", "example" sections for how-tos
- Math posts use `$$...$$` for MathJax formulas

## Key tools in Pavel's workflow

- Wolfram Mathematica / Wolfram Language — primary computational tool
- LaTeX (amsart class, Palatino font) — for structured research notes
- Claude Code + Cowork mode — AI-assisted research
- MCP servers: Wolfram, arXiv, Crossref, Desktop Commander
- Custom Cowork skills: wolfram-research-project, wi-invoice, skill-creator

## Skills (in /mnt/.skills/skills/)

- `wolfram-research-project/` — scaffolds research projects with standard folder structure
- `wi-invoice/` — generates monthly consulting invoices from Apple Mail weekly reports
- `skill-creator/` — meta-skill for creating/improving other skills
