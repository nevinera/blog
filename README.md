# blog

The source for [blog.nevinera.dev](https://blog.nevinera.dev), built with Jekyll.

## Run it locally

```sh
bundle install
bundle exec jekyll serve --livereload --drafts
```

Then open http://localhost:4000.

## Write a post

Add a file named `_posts/YYYY-MM-DD-some-title.md`:

```markdown
---
title: Some title
tags: [delve]
---

The post goes here.
```

Put unfinished posts in `_drafts/`, without the date in the filename.

Use lowercase, single-word or hyphenated tags. Each tag gets a page at `/tags/<tag>/` and a feed at `/feed/by_tag/<tag>.xml`.

Put images in `assets/images/`. Host video somewhere else.

## Publish

Pushing to `main` builds and deploys the site through GitHub Pages.
