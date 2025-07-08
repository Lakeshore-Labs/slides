# Company Presentations

This repository serves as the **central hub for all company presentations**. It contains Hugo-based presentations using the reveal.js theme, making it easy to create, maintain, and deploy professional slide presentations for our organization.

## Overview

This project uses [Hugo](https://gohugo.io/) with the [reveal-hugo](https://github.com/dzello/reveal-hugo) theme to create beautiful slide presentations that can be viewed in any web browser. All presentations are stored in a single repository for easy management and consistent styling across the organization.

## Prerequisites

- [Hugo](https://gohugo.io/getting-started/installing/) (extended version recommended)
- [Git](https://git-scm.com/)

## Quick Start

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd presentations
   ```

2. Initialize and update git submodules:
   ```bash
   git submodule update --init --recursive
   ```

3. Run the Hugo development server:
   ```bash
   hugo server
   ```

4. Open your browser to `http://localhost:1313` to view the presentations

5. **For GitHub Pages deployment**: Simply push your changes to the `main` branch and GitHub Actions will automatically build and deploy your site!

## Creating a New Presentation

To create a new presentation for the company, simply add a new directory to the `content/` folder:

### Step 1: Create the Presentation Directory

```bash
mkdir content/[presentation-name]
```

**Naming Convention**: Use descriptive, lowercase names with hyphens (e.g., `quarterly-review`, `product-launch`, `team-training`).

### Step 2: Create the Presentation Content

Create an `_index.md` file in your new directory with your presentation content:

```markdown
---
title: "Your Presentation Title"
theme: "white"
date: 2024-01-01
author: "Your Name"
---

# Your Presentation Title

Welcome to the presentation!

---

## Slide 2

This is the second slide.

---

## Slide 3

Add more content here...
```

### Step 3: Preview Your Presentation

1. Start the Hugo development server:
   ```bash
   hugo server
   ```

2. Navigate to `http://localhost:1313/[presentation-name]/` to view your presentation

### Step 4: Add Assets (Optional)

If your presentation includes images or other assets:

1. Create a static folder for your assets:
   ```bash
   mkdir static/images/[presentation-name]
   ```

2. Add your images and reference them in your presentation:
   ```markdown
   ![Image Description](/images/[presentation-name]/your-image.jpg)
   ```

## Existing Presentations

Browse the `content/` directory to see all available presentations:

```
content/
├── bundle-example/          # Example of bundled presentation
├── cafe/                    # Cafe-themed presentation
├── custom-theme-example/    # Custom theme demonstration
├── docs/                    # Documentation presentation
├── home/                    # Home page content
├── logo-example/            # Logo integration example
├── plugin-example/          # Plugin usage examples
├── section-example/         # Section-based presentation
├── template-example/        # Template usage example
└── trainer/                 # Training presentation
```

Each directory represents a separate presentation that can be accessed at `http://localhost:1313/[directory-name]/`.

## Building for Production

To build the static site for deployment:

```bash
hugo --minify
```

The generated files will be in the `public/` directory.

## GitHub Pages Deployment

This project is configured to automatically deploy to GitHub Pages using GitHub Actions.

### Setup Instructions

1. **Enable GitHub Pages** in your repository settings:
   - Go to your repository → Settings → Pages
   - Under "Source", select "GitHub Actions"

2. **Push to main branch** - The workflow will automatically trigger and deploy your site

3. **View your presentations** at: `https://[your-username].github.io/[repository-name]/`

### Automatic Deployment

The GitHub Actions workflow (`.github/workflows/hugo-deploy.yml`) will:
- ✅ Trigger on every push to the `main` branch
- ✅ Install Hugo and build dependencies
- ✅ Checkout code including git submodules (for the reveal-hugo theme)
- ✅ Build the Hugo site with minification
- ✅ Deploy to GitHub Pages automatically

### Manual Deployment

You can also trigger the deployment manually:
- Go to Actions tab in your GitHub repository
- Select "Deploy Hugo site to GitHub Pages"
- Click "Run workflow"

## Presentation Features

- **Slide Navigation**: Use arrow keys or click navigation arrows
- **Speaker Notes**: Press `s` to open speaker notes view
- **Overview Mode**: Press `Esc` to see all slides at once
- **Zoom**: Press `Alt+Click` to zoom in/out
- **Print**: Add `?print-pdf` to URL for print-friendly version

## Customization

### Themes

Available themes can be set in the front matter of your presentation:
- `black`, `white`, `league`, `beige`, `sky`, `night`, `serif`, `simple`, `solarized`

### Custom CSS

Add custom styles in `assets/custom-theme.scss` or create theme-specific CSS files.

### Plugins

The theme includes several reveal.js plugins:
- Highlight.js for syntax highlighting
- Math support with KaTeX
- Mermaid for diagrams
- Speaker notes

## Directory Structure

```
presentations/
├── content/           # Presentation content
├── static/           # Static assets (images, etc.)
├── layouts/          # Custom layouts (if needed)
├── assets/           # CSS/SCSS files
├── data/             # Data files
├── themes/           # Hugo themes (reveal-hugo)
└── config.toml       # Hugo configuration
```

## Tips

- Use `---` to create new slides
- Use `--` to create vertical slides
- Include images in `static/images/` and reference them as `/images/filename.jpg`
- Use shortcodes like `{{< frag >}}` for fragment animations

## Support

For Hugo-specific issues, see [Hugo Documentation](https://gohugo.io/documentation/)
For reveal.js features, see [reveal.js Documentation](https://revealjs.com/)
For theme-specific features, see [reveal-hugo Documentation](https://github.com/dzello/reveal-hugo) 