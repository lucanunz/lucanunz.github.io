# Customizing the Projects section

The Projects section is currently **hidden** from the site navigation. This guide
explains how to populate it and turn it back on.

## How it works

- The page itself lives in [`_pages/projects.md`](_pages/projects.md). It only contains
  layout logic — you normally don't edit the body.
- The actual project entries are individual Markdown files in the
  [`_projects/`](_projects/) folder. Each file is one project card.
- Cards are grouped by their `category` and ordered by `importance` (lower number =
  shown first). The page decides which categories to display via the
  `display_categories` list in the front matter of `_pages/projects.md`.

There are already four starter entries in `_projects/` (`1_project.md` … `4_project.md`)
based on your CV. Use them as templates.

## Re-enabling the section

1. Open [`_pages/projects.md`](_pages/projects.md) and change the front matter:
   ```yaml
   nav: true # was: false
   ```
   `nav_order` controls where it appears in the top navigation (relative to the
   other pages: publications = 2, repositories = 4, cv = 5).

2. Rebuild (`bundle exec jekyll build`) or just refresh if running `bundle exec jekyll serve`.

## Editing or adding a project

Each file in `_projects/` looks like this:

```markdown
---
layout: page
title: My project title
description: One-line summary shown on the card.
img: assets/img/1.jpg        # card thumbnail (optional; omit for no image)
importance: 1                # ordering within its category (lower = first)
category: research           # must be listed in display_categories to show
related_publications: true   # optional: auto-links matching papers from papers.bib
---

Free-form Markdown body shown on the project's own page.
You can embed images, videos, code blocks, etc.
```

Key fields:

- **`category`** — group label. The page shows the categories listed in
  `display_categories` in `_pages/projects.md` (currently `[research]`). To add a new
  group, e.g. `software`, add `category: software` to a project file **and** add
  `software` to `display_categories`.
- **`img`** — path to a thumbnail under `assets/img/`. Drop your own image there and
  point to it. Leave the field empty (`img:`) for a text-only card.
- **`importance`** — sort order inside the category.
- **`related_publications: true`** — pulls in citations from `_bibliography/papers.bib`
  that share authors/keywords. Remove it if you don't want that.

To add a project, copy an existing file (e.g. `cp _projects/1_project.md _projects/5_project.md`)
and edit it. To remove one, delete its file.

## Images

To add real project images, place them in `assets/img/` and reference them with
`img: assets/img/yourfile.jpg`. The site auto-generates responsive WebP versions at
build time (ImageMagick must be installed).
