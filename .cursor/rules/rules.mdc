# Cursor Rules for Company Presentations

## Project Context
This is a Hugo-based presentation repository that serves as the central hub for all company presentations. It uses the reveal-hugo theme with reveal.js to create beautiful slide presentations.

## Core Rules

### 1. Presentation Creation Workflow
When a user requests to create a new presentation:
1. **Always create a new directory** in the `content/` folder
2. **Use naming conventions**: lowercase with hyphens (e.g., `quarterly-review`, `product-launch`, `team-training`)
3. **Create an `_index.md` file** with proper front matter
4. **Guide the user through the complete setup** including themes, assets, and content structure

### 2. Front Matter Template
Always use this front matter template for new presentations:
```markdown
---
title: "Presentation Title"
theme: "white"
date: 2024-01-01
author: "Author Name"
---
```

### 3. Available Themes
When suggesting themes, use these reveal.js themes:
- `black`, `white`, `league`, `beige`, `sky`, `night`, `serif`, `simple`, `solarized`

### 4. Slide Structure Guidelines
- Use `---` to create new horizontal slides
- Use `--` to create vertical slides (sub-slides)
- Keep slides focused and concise
- Use fragment animations with `{{< frag >}}` shortcode when appropriate

### 5. Asset Management
For presentations with images or other assets:
- Create organized directories: `static/images/[presentation-name]/`
- Reference images with: `/images/[presentation-name]/filename.jpg`
- Suggest WebP format for better performance when possible

### 6. Content Organization
- Each presentation should be in its own directory under `content/`
- Use descriptive directory names that reflect the presentation topic
- Include proper metadata in front matter for organization

### 7. Development Workflow
Always remind users to:
1. Run `hugo server` to start the development server
2. Navigate to `http://localhost:1313/[presentation-name]/` to view
3. Use browser developer tools to test responsiveness
4. Test slide navigation and features before deployment

### 8. Best Practices
- **Responsive Design**: Ensure content works on different screen sizes
- **Accessibility**: Use proper heading hierarchy and alt text for images
- **Performance**: Optimize images and minimize slide content
- **Consistency**: Use consistent styling across company presentations

### 9. Shortcodes and Features
Guide users on using reveal-hugo shortcodes:
- `{{< slide >}}` for slide-specific configuration
- `{{< frag >}}` for fragment animations
- `{{< note >}}` for speaker notes
- `{{< section >}}` for section dividers

### 10. File Structure Awareness
When creating presentations, be aware of:
- `config.toml` for site-wide configuration
- `layouts/` for custom layouts if needed
- `assets/` for custom CSS/SCSS
- `data/` for data files
- `static/` for static assets

## Example Commands to Suggest

### Creating a New Presentation
```bash
# Create presentation directory
mkdir content/my-presentation

# Create the main presentation file
touch content/my-presentation/_index.md

# Create assets directory if needed
mkdir -p static/images/my-presentation
```

### Running Development Server
```bash
hugo server
```

### Building for Production
```bash
hugo --minify
```

## Common Patterns

### Basic Presentation Structure
```markdown
---
title: "My Presentation"
theme: "white"
date: 2024-01-01
author: "Your Name"
---

# My Presentation

Welcome slide content

---

## Agenda

- Point 1
- Point 2
- Point 3

---

## Main Content

Your main content here

---

## Thank You

Questions?
```

### Presentation with Images
```markdown
## Slide with Image

![Description](/images/my-presentation/chart.png)

Key points about the image
```

### Presentation with Code
```markdown
## Code Example

```javascript
function hello() {
    console.log("Hello, World!");
}
```
```

## Troubleshooting Guidelines

### Common Issues to Address
1. **Submodule Issues**: If theme doesn't load, suggest `git submodule update --init --recursive`
2. **Server Issues**: If Hugo server fails, check Hugo version and suggest using extended version
3. **Asset Loading**: If images don't load, verify paths and suggest checking static folder structure
4. **Theme Issues**: If theme doesn't apply, verify theme name in front matter

### Deployment Considerations
- GitHub Pages deployment is automatic on push to main branch
- Build process uses GitHub Actions
- Minification is handled automatically in production

## Documentation References
- Point users to existing presentations in `content/` for examples
- Reference Hugo documentation for advanced features
- Mention reveal.js documentation for presentation features
- Highlight the reveal-hugo theme documentation for specific shortcodes

## Quality Assurance
Before marking a presentation as complete:
1. Verify all slides render correctly
2. Check navigation works properly
3. Test on different screen sizes
4. Ensure all assets load correctly
5. Validate front matter syntax
6. Check for typos and formatting issues 