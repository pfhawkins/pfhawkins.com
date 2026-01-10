# Hugo Static Site - Agent Development Guide

This is a Hugo static site generator project for P.F. Hawkins' personal blog and commonplace book.

## Build, Test, and Development Commands

### Core Hugo Commands
```bash
# Build the site to public/ directory
hugo

# Start development server with live reload
hugo server -D

# Build without drafts (production)
hugo --minify

# Clean public directory before build
hugo --cleanDestinationDir

# Check site for issues
hugo check
```

### Single Content Testing
```bash
# Build with drafts and future posts
hugo server -D --buildDrafts --buildFuture

# Test specific file changes (Hugo auto-reloads)
# Edit any file in content/, layouts/, or static/ and Hugo will rebuild
```

### Deployment
```bash
# Deploy (if configured)
hugo deploy --target "production"

# Build for production
hugo --minify
```

## Project Structure

```
├── config.toml          # Hugo configuration
├── content/             # Markdown content files
│   ├── about/          # About page
│   └── blog/           # Blog posts (mixed .md/.markdown extensions)
├── layouts/            # HTML templates
│   ├── _default/       # Default templates
│   ├── partials/       # Reusable template parts
│   └── shortcodes/     # Custom shortcodes
├── static/             # Static assets (CSS, JS, images)
│   ├── stylesheets/    # CSS files
│   └── javascripts/    # JavaScript files
└── public/            # Generated site (don't edit)
```

## Code Style Guidelines

### Hugo Templates (HTML)
- Use Hugo template syntax: `{{ .Variable }}` and `{{ partial "name.html" . }}`
- Follow Tachyons CSS classes for styling
- Use semantic HTML5 tags appropriately
- Keep templates focused on structure, not content
- Include `{{ partial "header.html" . }}` and `{{ partial "footer.html" . }}` in main templates

### Front Matter (Content Files)
- Use TOML format with `+++` delimiters (current standard)
- Legacy content uses YAML with `---` delimiters
- Required fields: `title`, `date`, `categories`
- Optional fields: `tags`, `slug`, `draft`, `heading`
- Use kebab-case for slugs and categories

### CSS/Styling
- Primarily uses Tachyons CSS framework via CDN
- Custom CSS goes in `static/stylesheets/` (currently has `screen.css`)
- Additional CSS loaded via config.toml: `/css/override.css`
- Use utility-first approach with Tachyons classes

### JavaScript
- Legacy scripts in `static/javascripts/` (jQuery-based)
- Modern JS embedded directly in templates
- Use defer/async appropriately for performance
- Use defer/async appropriately for performance

### File Naming
- Blog posts: `YYYY-MM-DD-title.md` or `YYYY-MM-DD-title.markdown`
- Templates: `snake_case.html` for partials
- Static assets: use descriptive names with appropriate extensions

### Content Organization
- Categories: major content groupings (e.g., "essay", "review")
- Tags: specific topics or keywords
- Use taxonomy lists for navigation (see `categories/terms.html`, `tags/terms.html`)

## Configuration Notes

### Site Parameters (config.toml)
- `baseurl`: Production URL (update when deploying)
- `title`: Site title
- `description`: Site description for SEO
- `author`: Author name
- `dateform`: Date format for display
- `extracssfiles`: Additional CSS files to load

### Content Processing
- Uses Blackfriday markdown processor
- Pygments for syntax highlighting with CSS classes
- RSS feeds auto-generated for main content

## Development Workflow

1. Create/edit content in `content/`
2. Run `hugo server -D` for development
3. Test changes locally at `localhost:1313`
4. Use `hugo --minify` for production builds
5. Deploy `public/` directory to web server

## Common Patterns

### New Blog Post
```bash
# Create new post with current date
hugo new blog/$(date +%Y-%m-%d)-post-title.md
```

### Template Inclusion
```html
{{ partial "header.html" . }}
{{ partial "page-heading.html" . }}
{{ .Content }}
{{ partial "footer.html" . }}
```

### Category/Tag Navigation
```html
{{ range .Params.categories }}
<a href="/categories/{{ . }}/" class="link dim red">{{ . }}</a>
{{ end }}
```

## Testing Strategy
- Visual testing via `hugo server`
- Validate HTML structure in browser
- Test responsive design using browser dev tools
- Check RSS feed generation
- Verify internal links resolve correctly

## Performance Considerations
- Use CDN resources (Tachyons, external scripts)
- Optimize images in static/
- Enable minification for production builds
- Consider lazy loading for heavy content