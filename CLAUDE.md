# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Hugo-based presentation system using the reveal-hugo theme for creating slide presentations. The repository serves as a central hub for company presentations built on reveal.js, deployed automatically to GitHub Pages.

## Development Commands

### Core Development
- `hugo server` - Start development server (accessible at http://localhost:1313)
- `hugo --minify` - Build production site (outputs to `/public` directory)
- `hugo server --disableFastRender` - Development server with full rebuilds

### Deployment
- Automatic deployment via GitHub Actions on push to `main` branch
- Manual deployment: Push to `main` or trigger "Deploy Hugo site to GitHub Pages" workflow
- Production site: https://slides.vlogical.ai

## Architecture

### Hugo Module System
- Uses Go modules for theme management (`go.mod`, `go.sum`)
- Theme: `github.com/joshed-io/reveal-hugo` (reveal.js integration)
- Workspace setup via `hugo.work` for local development

### Content Structure
- Each presentation = directory in `/content/`
- Presentation entry point: `_index.md` with reveal.js front matter
- Multilingual support: English (default), Vietnamese, Arabic with RTL support
- Markdown slides separated by `---` (horizontal) and `--` (vertical)

### Configuration Hierarchy
- `config.toml` - Global Hugo and reveal.js settings
- Front matter in `_index.md` - Per-presentation configuration
- Templates in `params.reveal_hugo.templates` for reusable configurations

### Theme System
- Built-in themes: `black`, `white`, `league`, `beige`, `sky`, `night`, `serif`, `simple`, `solarized`
- Custom themes: `/assets/custom-theme.scss` and `/static/reveal-hugo/themes/`
- Theme selection via front matter `[reveal_hugo] theme = "themename"`

### Assets & Static Files
- `/static/` - Images, CSS, JS, plugins (copied as-is to output)
- `/assets/` - SCSS files processed by Hugo
- `/layouts/partials/` - Custom reveal.js layout overrides per presentation

### Presentation Features
- Fragment animations: `{{% fragment %}}` shortcode
- Background media: `{{% slide background-image="..." %}}` or `background-video`
- Speaker notes, math support (KaTeX), syntax highlighting
- Gallery plugin, Mermaid diagrams support

## Creating New Presentations

1. Create directory: `mkdir content/[presentation-name]`
2. Add `_index.md` with reveal.js front matter:
   ```yaml
   +++
   title = "Presentation Title"
   outputs = ["Reveal"]
   [reveal_hugo]
   theme = "white"
   +++
   ```
3. Add slides with `---` separators
4. Test with `hugo server`
5. Deploy by pushing to `main`

## Git Workflow

- Main branch: `main`
- Auto-deploy on push to `main`
- Submodules handled automatically in GitHub Actions
- Modified files tracked (current: `content/ollin/_index.md`)