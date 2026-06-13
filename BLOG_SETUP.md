# Customizing the Blog section

The Blog is currently **hidden** from the site navigation, and the "latest posts"
block on the homepage is turned off. This guide explains how to write posts and turn
it back on.

## How it works

- The blog listing page is [`_pages/blog.md`](_pages/blog.md) (layout/pagination logic;
  you don't normally edit the body).
- Individual posts are Markdown files in the [`_posts/`](_posts/) folder.
- The filename **must** follow Jekyll's convention: `YYYY-MM-DD-title.md`
  (e.g. `2026-06-13-my-first-post.md`). The date in the filename sets the post date.
- The homepage can also show a short "latest posts" list — controlled separately in
  [`_pages/about.md`](_pages/about.md).

There are example posts already in `_posts/` (shipped with the theme) that demonstrate
images, math, code, citations, etc. You can study them and then delete the ones you
don't want.

## Re-enabling the section

1. Show the Blog tab in the nav — open [`_pages/blog.md`](_pages/blog.md) and set:
   ```yaml
   nav: true # was: false
   ```

2. (Optional) Re-enable the "latest posts" block on the homepage — open
   [`_pages/about.md`](_pages/about.md) and set:
   ```yaml
   latest_posts:
     enabled: true # was: false
   ```

3. Rebuild (`bundle exec jekyll build`) or refresh your `bundle exec jekyll serve` session.

## Writing a post

Create a file `_posts/2026-06-13-hello-world.md`:

```markdown
---
layout: post
title: Hello world
date: 2026-06-13 10:00:00+0900
description: An optional one-line summary.
tags: robotics research
categories: notes
---

Your post content in Markdown.
```

Useful front-matter options:

- **`tags`** / **`categories`** — space-separated; power the tag/category archive pages.
- **`featured: true`** — pins the post to the top of the blog index.
- **`giscus_comments: true`** — enables comments (needs the `giscus:` block in
  `_config.yml` to be filled in with your repo info).
- **`related_posts: false`** — hides the "related posts" list at the bottom.

To remove the example posts, delete the unwanted files in `_posts/`.

## Tidying up the example content

The theme ships demo posts (and the homepage `external_sources` in `_config.yml` pulls
in sample Medium/Google posts). Once you start blogging, you'll likely want to:

- Delete the demo files in `_posts/` you don't want.
- Remove or replace the `external_sources:` entries in `_config.yml` (they currently
  point at al-folio's own Medium feed and a sample Google blog post).
