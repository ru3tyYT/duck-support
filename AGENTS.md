# AGENTS.md - Troubleshooting Hub

## Project Overview

This is a documentation site for Revolution Macro and RDP troubleshooting guides, built with MkDocs and Material for MkDocs.

## Tech Stack

- **Static Site Generator**: MkDocs
- **Theme**: Material for MkDocs
- **Hosting**: GitHub Pages

## Directory Structure

```
duck-support/
├── docs/                       # Documentation source
│   ├── index.md              # Homepage
│   ├── revolution-macro/      # Revolution Macro section
│   │   ├── index.md
│   │   └── installation.md
│   ├── rdp-troubleshooting/  # RDP troubleshooting section
│   │   ├── index.md
│   │   ├── rdp-setup.md
│   │   ├── rdp-wrapper.md
│   │   ├── common-errors.md
│   │   └── connection-issues.md
│   ├── optimization/           # Optimization section
│   │   └── index.md
│   └── assets/
│       └── images/            # Documentation images
│           ├── rdp/
│           └── optimization/
├── mkdocs.yml                 # MkDocs configuration
├── .gitignore
└── site/                      # Built site (generated)
```

## Adding New Content

### Creating a New Article

1. Create a new `.md` file in the appropriate section folder
2. Add frontmatter at the top:
   ```markdown
   ---
   title: Your Article Title
   description: Brief description
   ---
   
   # Your Article Title
   ...
   ```

3. Add the article to `mkdocs.yml` under the appropriate `nav` section

### Adding Images

1. Place images in `docs/assets/images/[section]/`
2. Reference with relative path from the markdown file:
   ```
   ![Alt text](../../assets/images/section/image.png)
   ```

Note: Go up 2 directories from the article to reach assets.

## MkDocs Configuration

Located in `mkdocs.yml`:

- **Navigation**: Sections appear in sidebar
- **Features enabled**: Search, instant navigation, table of contents
- **Dark/Light mode**: Available via palette toggle

## Important Conventions

### Image Paths
When referencing images in articles located in subdirectories (like `rdp-troubleshooting/`), use:
- From `docs/rdp-troubleshooting/article.md`: `../../assets/images/rdp/image.png`
- NOT: `../assets/images/rdp/image.png` (missing one level)

### Icon Syntax
Do NOT use Material icons with `:icon-name:` syntax - it requires extra plugins. Use simple text or emoji instead:
- ✅ `[View Articles →](link)`
- ❌ `[View Articles :material-arrow-right:](link)`

### Admonitions
Use MkDocs admonitions for callouts:
```markdown
!!! tip "Title"
    Content here

!!! warning "Warning"
    Content here
```

Types: tip, warning, note, danger

### Code Blocks
Use fenced code blocks with language specified:
```markdown
```cmd
some command
```
```

## Running Locally

```bash
# Install dependencies (if needed)
pip install mkdocs-material

# Serve locally
mkdocs serve

# Build for production
mkdocs build
```

## Building and Deploying

1. Run `mkdocs build` to generate the `site/` folder
2. Push to GitHub - GitHub Pages will auto-deploy from `main` branch
3. Site URL: https://ru3tyyt.github.io/duck-support/

## Git Workflow

### Making Changes
1. Create a new branch for features
2. Make changes
3. Test with `mkdocs serve`
4. Commit in small, focused commits
5. Push and create PR

### Commit Message Style
- Use clear, descriptive commit messages
- Example: `Add RDP Setup Guide article`

### Important Files
- `mkdocs.yml` - Configuration (careful editing)
- `docs/` - All content
- `docs/index.md` - Homepage

## Importing New Content

When importing new Markdown files:

1. Review the original content for structure
2. Restructure for MkDocs (frontmatter, headers, admonitions)
3. Extract any embedded images (base64) to files
4. Add to appropriate section
5. Update navigation in `mkdocs.yml`
6. Update homepage if needed

## Troubleshooting

### Images not loading
- Check path is correct (go up 2 directories from article)
- Ensure image file exists in `docs/assets/images/`
- Check for typos in filename

### Build warnings
- Missing navigation entries: Add to `nav` in mkdocs.yml
- Broken internal links: Verify relative paths

### Search not working
- Rebuild with `mkdocs build`
- Check search is enabled in mkdocs.yml
