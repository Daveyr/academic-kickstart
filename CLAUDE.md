# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build and Development Commands

### Hugo Commands
- **Run development server:** `hugo server -D` (includes drafts) or `hugo server`
- **Build production site:** `hugo --gc --minify`
- **Check Hugo version:** `hugo version` (Required: >= 0.80.0 as per `netlify.toml`)

### R / blogdown (for .Rmd files)
This project uses `blogdown` for RMarkdown content. Hugo ignores `.Rmd` files directly (see `config.toml`); they must be rendered to `.html` in R first.
- **Serve site from R:** `Rscript -e "blogdown::serve_site()"`
- **Build site from R:** `Rscript -e "blogdown::build_site()"`
- **Render a single post:** `Rscript -e "blogdown::build_site(build_rmd = 'content/post/path/to/file.Rmd')"`

## Code Architecture

### Overview
This is a [Wowchemy/Academic](https://wowchemy.com) site built with [Hugo](https://gohugo.io). It uses a modular configuration and a widget-based homepage system.

### Key Directories
- `config/_default/`: Core settings split into `params.toml` (UI/Features), `menus.toml` (Navigation), and `languages.toml` (Multilingual).
- `content/home/`: Contains Markdown files that act as "widgets" for the homepage. The `active` parameter in each file toggles its visibility.
- `content/post/`, `content/project/`, `content/publication/`: Main content collections.
- `assets/scss/custom.scss`: Location for custom CSS/SASS overrides.
- `layouts/`: Custom HTML templates. `layouts/partials/` contains reusable components.
- `static/`: Files served directly (images, PDFs, etc.).

### Development Patterns
- **Home Page:** To modify the homepage, edit files in `content/home/` rather than a single `index.md`.
- **Theming:** Customizations should be done in `assets/` or `layouts/` to override the `starter-academic` theme without modifying the theme files directly.
- **Configuration:** Always check `config/_default/params.toml` first for site-wide feature toggles (math, highlight, etc.).
- **RMarkdown:** Posts authored in `.Rmd` generate a corresponding `.html` file. Hugo uses the `.html` file for the build.
