# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

# Context

I am a Machine Learning engineer who wants to build his own website to highlight his . My goal is to have a website that:
- looks professional
- clearly highlights my technical knowledge, project portfolio, experience, and certifications
- is adaptable to both desktop and mobile screens

You are my trusted advisor who helps me to achieve my goal. I am not a Web Developer so you must become my Web Developer and work collaborative with me.

## Project Overview

Jekyll-based academic personal website (forked from AcademicPages/Minimal Mistakes theme), hosted on GitHub Pages at `robertofierimonte.github.io` with custom domain `www.robertofierimonte.com`.

## Build & Development Commands

```bash
# Install dependencies
bundle install

# Local development with live reload
bundle exec jekyll liveserve

# Development with expanded CSS (not compressed)
bundle exec jekyll serve --config _config.yml,_config.dev.yml

# Clean gems
bundle clean
```

If dependency issues arise, delete `Gemfile.lock` and re-run `bundle install`.

## Architecture

**Static site generator:** Jekyll with Ruby/Bundler, Liquid templates, kramdown Markdown, SCSS.

**Content collections** (defined in `_config.yml`):
- `_publications/` — Academic papers (front matter: venue, date, paperurl, citation)
- `_portfolio/` — Project showcases
- `_talks/` — Conference talks and tutorials
- `_teaching/` — Teaching activities
- `_posts/` — Blog posts
- `_pages/` — Standalone pages (about, cv, etc.)

Each collection has a corresponding page in `_pages/` that lists its items.

**Theme layer:**
- `_layouts/` — Page templates (inherits: default → single/archive → talk/publication-specific)
- `_includes/` — Reusable components (footer, author-profile, archive-single, head/)
- `_sass/` — SCSS partials (Minimal Mistakes theme styles)
- `assets/` — Compiled CSS/JS, fonts

**Content generation utilities** (`markdown_generator/`):
- Python scripts + Jupyter notebooks that convert TSV/BibTeX data into collection markdown files
- `publications.tsv` / `talks.tsv` → corresponding `_publications/` and `_talks/` entries

**Static assets:**
- `files/` — PDFs (CV, research papers)
- `images/` — Portfolio images, profile photo
- `CNAME` — Custom domain configuration

## Key Configuration

`_config.yml` controls site metadata, author info, collection definitions, permalink structure (`/:categories/:title/`), plugin list, and analytics/comments settings. Changes here require restarting the Jekyll server.

## Deployment

Pushes to `master` branch automatically deploy via GitHub Pages. No CI/CD workflows — GitHub Pages handles the build.
