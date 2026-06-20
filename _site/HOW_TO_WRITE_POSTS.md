How to write posts for this Jekyll site
======================================

This guide explains the conventions used in this repository so you can add new blog posts or event posts that integrate with the site layout and language selector.

Where to place posts
- Place post files in the `_posts/` directory.
- Filenames must use Jekyll's format: `YEAR-MONTH-DAY-title.md` (example: `2026-06-18-mi-evento.md`).

Required front matter
---------------------
Add YAML front matter at the top of each post. Minimal example:

```
---
layout: post
title: "Mi título de evento"
date: 2026-06-18 10:00:00 +0200
lang: es
ref: my-event-unique-ref
author: "Nombre"
categories: eventos
tags: [conferencia, gratis]
excerpt: "Resumen corto para listados."
image: /assets/images/mi-evento.jpg
---
```

- `layout`: use `post` (or whatever layout your theme expects).
- `title`: human-readable title.
- `date`: used for sorting and permalink generation.
- `lang`: `es` (Spanish) or `eu` (Euskara). The site uses `page.lang` in templates.
- `ref`: a short identifier shared between translations (see below).
- `categories` / `tags`: used by the site to group and list posts.
- `excerpt` and `image`: optional metadata used by index and social cards.

Writing content
---------------
- Write content in Markdown. Use standard GitHub-flavored Markdown for headings, lists, code blocks, images, etc.
- Store images under `assets/images/` and link them with absolute paths, e.g. `/assets/images/mi-evento.jpg` so Jekyll's `relative_url` works consistently.
- You can use Liquid inside posts if you need dynamic values, but prefer plain Markdown for portability.
- For math, use KaTeX notation (this repo's templates render KaTeX where configured). Wrap inline math with `$...$` and display math with `$$...$$`.

Translations / multilingual notes
-------------------------------
- To create a translation of a post, create another post file with the same `ref` value and `lang` set to the other language (for example one with `lang: es` and one with `lang: eu`).
- Example: two files with the same `ref: my-event-unique-ref` but different `lang` and translated `title`/content.
- Note: the site header currently looks for pages with matching `ref` to build the language selector. If you need the language selector to switch between posts, adapt `_includes/header.html` to search `site.posts` (instead of `site.pages`), or create page wrappers that reference the posts.

Permalinks and linking
----------------------
- Jekyll will build permalinks from your post's date and slug by default. Use `{{ post.url | relative_url }}` in templates to link safely.

Preview locally
---------------
To preview the site locally (requires Ruby + Bundler + the Gemfile in repo):

```bash
bundle install
bundle exec jekyll serve --livereload
```

Then open http://127.0.0.1:4000 in your browser.

Good practices
--------------
- Keep `ref` values short and unique (use hyphenated slugs).
- Write a short `excerpt` (1 sentence) used for lists and RSS.
- Add an `image` at 1200×630 for good social previews.
- Use `tags` consistently so listings and filters work.

If you want, I can also:
- Add a post template file under `_drafts/` or `CONTRIBUTING.md` with copy-paste front matter.
- Update `_includes/header.html` to support language switching for posts.
