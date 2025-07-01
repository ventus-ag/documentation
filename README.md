# EWW | ITandTEL Cloud Documentation

Documentation for the EWW | ITandTEL Cloud platform (docs.ventuscloud.eu), built with Hugo using the hugo-theme-learn theme.

## 🚀 Quick Start

### Requirements
- [Hugo Extended](https://gohugo.io/getting-started/installing/) version 0.147.9+ 
- Git

### Check Hugo Installation
```bash
hugo version
```

Should show: `hugo v0.147.9+extended` or newer

### Update Hugo (if needed)
```bash
# For macOS with Homebrew
brew update && brew upgrade hugo

# For other systems, visit: https://gohugo.io/installation/
```

### Local Development
```bash
# Clone the repository
git clone <repository-url>
cd documentation

# Start local development server
hugo server -D --navigateToChanged
```

Site will be available at: **http://localhost:1313/**

### Alternative Launch Commands
```bash
# Standard run without drafts
hugo server

# Run with specific IP binding
hugo server --bind 0.0.0.0 --baseURL http://your-ip:1313

# Full rebuild on changes (slower)
hugo server --disableFastRender
```

## 📁 Project Structure

```
documentation/
├── content/                    # Documentation content
│   ├── _index.md              # Homepage
│   ├── getting-started/       # Chapter 1: Getting started
│   ├── identity-management/   # Chapter 2: User management
│   ├── products/              # Chapter 3: Cloud services
│   ├── iac/                   # Chapter 4: Infrastructure as Code
│   ├── tutorials-advanced/    # Chapter 5: Advanced scenarios
│   └── assets/images/         # Images organized by service
├── static/css/                # Custom styles
├── layouts/partials/          # Custom templates
├── themes/hugo-theme-learn/   # Base theme
└── config.toml               # Hugo configuration
```

## ✏️ Development Workflow

### Creating New Content
1. Create `.md` file in appropriate `/content/` directory
2. Add TOML front matter:
```toml
+++
title = "Page Title"
date = 2019-09-25T01:53:09+03:30
weight = 10
+++
```

### Adding Images
1. Place images in `/content/assets/images/service-name/`
2. Use relative paths:
```markdown
![Description](mdc:../../assets/images/service-name/1.png?width=30pc&classes=border,shadow)
```

### Chapter Structure
- **Index pages** (`_index.md`): add `chapter = true` and `{{% children %}}`
- **Regular pages**: content only without `chapter = true`

## 🛠️ Common Issues

### Hugo Version Compatibility
This documentation requires Hugo v0.147.9+ for compatibility with GitHub Pages deployment. If you have an older version:

```bash
# Check current version
hugo version

# Update Hugo (macOS with Homebrew)
brew update && brew upgrade hugo

# Verify update
hugo version
```

**Note**: Hugo v0.124.0+ deprecated `.Site.IsMultiLingual` in favor of `hugo.IsMultilingual`. Our theme files have been updated to use the modern syntax.

### Site not accessible at localhost:1313
1. Ensure Hugo server started without errors
2. Check that port 1313 is available
3. Try different port: `hugo server -p 1314`

### Images not displaying
Check:
- Correct relative paths
- Files exist in `/content/assets/images/`
- Proper Markdown image syntax

## 🎨 Customization

### Styles
Edit only `/static/css/theme-mine.css`

### Brand Colors
- Primary: `#0092cf`
- Hover: `#0078c0`
- Menu background: `#252c31`

### Configuration
Main settings in `config.toml`

## 📦 Production Build

```bash
# Generate static files
hugo

# Output in public/ folder
ls public/
```

## 🔍 Useful Commands

```bash
# Search content
grep -r "search term" content/

# Link checking (requires htmltest installation)
htmltest

# Clean Hugo cache
hugo mod clean

# Site statistics
hugo --printPathWarnings
```

## 📝 Conventions

### File Naming
- Use lowercase with hyphens: `virtual-machines.md`
- Images: `1.png`, `2.png`, `21-1.png`

### Content
- **Audience**: DevOps engineers, system administrators
- **Style**: Professional, technical, step-by-step instructions
- **Screenshots**: For every major step

### Front Matter
```toml
+++
title = "Descriptive Title"
date = 2019-09-25T01:53:09+03:30
weight = 10                    # Menu order (lower = higher)
chapter = true                 # Only for index pages
pre = "<b>1. </b>"            # Chapter numbering
+++
```

## 🚀 Deployment

Site automatically deploys to `docs.ventuscloud.eu` on changes to main branch using Hugo v0.147.9.

**Local & Remote Sync**: Both local development and GitHub Pages use the same Hugo version (v0.147.9+) for consistent behavior.

## 🤝 Contributing

1. Create branch for changes
2. Make changes and test locally
3. Ensure all links and images work
4. Create pull request

---

**Contact**: EWW | ITandTEL Cloud Technical Support