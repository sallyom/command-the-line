# How to Publish New Blog Posts

## Quick Start

### 1. Create a new post
```bash
# Create a new markdown file in content/posts/
# Make sure it has front matter at the top:
---
title: "Your Post Title"
date: 2025-11-18T20:00:00-05:00
draft: false
---
```

### 2. Build the site
```bash
hugo
```

### 3. Publish (two-step commit process)

**Step 1: Commit the published site**
```bash
cd public
git add .
git commit --signoff -m "Publish: Your post title

Co-Authored-By: Claude <noreply@anthropic.com>"
git push origin main
cd ..
```

**Step 2: Commit the source changes**
```bash
git add .
git commit --signoff -m "Add: Your post title

Co-Authored-By: Claude <noreply@anthropic.com>"
git push origin main
```

## Why two commits?

- `public/` is a git submodule pointing to `sallyom.github.io` (your published site)
- You commit there first to publish to GitHub Pages
- Then commit the parent repo to track which published version matches your source

## Your Blog URLs

- **Live site:** https://sallyom.github.io/
- **Source repo:** https://github.com/sallyom/command-the-line
- **Published repo:** https://github.com/sallyom/sallyom.github.io

## File Locations

- **Posts:** `content/posts/*.md`
- **About page:** `content/about.md`
- **Custom CSS:** `static/css/custom.css`
- **Config:** `config.toml`

## Notes

- It's normal to see "modified: public" in git status after committing in the public directory
- GitHub Pages may take a few minutes to update after pushing
- The site uses the hugo-kiera theme
