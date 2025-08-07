---
layout: page
title: Getting Started with Jekyll
nav_order: 1
parent: Tutorials
permalink: /tutorials/getting-started-with-jekyll/
---

# Getting Started with Jekyll

A beginner's guide to creating static sites with Jekyll and GitHub Pages.

## What is Jekyll?

Jekyll is a static site generator that transforms plain text files into websites. It's perfect for blogs, documentation sites, and portfolios.

## Prerequisites

- Ruby installed on your system
- Basic knowledge of Markdown
- Git for version control

## Installation

1. Install Jekyll:
   ```bash
   gem install jekyll bundler
   ```

2. Create a new Jekyll site:
   ```bash
   jekyll new my-site
   cd my-site
   ```

3. Start the development server:
   ```bash
   bundle exec jekyll serve
   ```

## Basic Structure

```
my-site/
├── _posts/          # Blog posts
├── _layouts/        # HTML templates
├── _includes/       # Reusable components
├── assets/          # CSS, JS, images
├── _config.yml      # Site configuration
└── index.md         # Homepage
```

## Creating Content

### Posts
Create files in `_posts/` with the format: `YYYY-MM-DD-title.md`

### Pages
Create markdown files in the root directory with front matter.

## Deployment

The easiest way to deploy is with GitHub Pages:

1. Push your code to GitHub
2. Enable GitHub Pages in repository settings
3. Your site will be available at `username.github.io/repository-name`

## Next Steps

- Customize themes
- Add plugins
- Set up custom domains
- Optimize for SEO

*This tutorial will be expanded with more detailed examples and advanced topics.*