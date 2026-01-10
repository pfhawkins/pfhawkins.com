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
# Edit any file in content/, layouts/, or assets/ and Hugo will rebuild
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
├── assets/             # Modern asset pipeline (CSS, JS processed by Hugo)
│   └── css/
│       └── styles.css  # Main Tailwind CSS file
├── static/             # Static assets (CSS, JS, images)
│   └── javascripts/    # Legacy JavaScript files
├── public/            # Generated site (don't edit)
├── package.json         # Node.js dependencies
└── hugo_stats.json      # Hugo class usage statistics
```

## Code Style Guidelines

### Hugo Templates (HTML)
- Use Hugo template syntax: `{{ .Variable }}` and `{{ partial "name.html" . }}`
- Follow Tailwind CSS utility classes for styling
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
- **Primary**: Uses Tailwind CSS v4.0.5 with Hugo integration
- **Asset Pipeline**: Hugo processes CSS via `css.TailwindCSS` function
- **Custom CSS**: Defined in `assets/css/styles.css` with custom utilities
- **Responsive Design**: Uses Tailwind's responsive prefixes (sm:, md:, lg:, xl:)
- **Custom Colors**: Define custom colors using `--color-*` variables in CSS

#### Key Tailwind Patterns
- Layout: `w-full max-w-full mx-auto` for full-width containers
- Spacing: `p-3 md:p-4` for responsive padding
- Typography: `text-2xl md:text-3xl` for responsive font sizes
- Colors: `text-red-600 hover:text-red-700` for consistent link styling
- Custom borders: `md:border-14 md:border-[#cdecff]` for responsive viewport borders

### JavaScript
- Legacy scripts in `static/javascripts/` (jQuery-based)
- Modern approach: Use defer/async appropriately for performance
- Consider modern framework-agnostic approaches

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
- `writeStats`: true (enables Hugo class usage tracking)
- `ignoreLogs`: ['warning-goldmark-raw-html'] (suppresses expected warnings)

### Content Processing
- **Markdown Processor**: Goldmark (default, CommonMark compliant)
- **Syntax Highlighting**: Pygments for syntax highlighting with CSS classes
- **RSS Feeds**: Auto-generated for main content
- **CSS Processing**: Hugo integrates with Tailwind CSS pipeline

### Tailwind Integration
- **Dependencies**: `@tailwindcss/cli` and `tailwindcss` in package.json
- **CSS Function**: Hugo's `css.TailwindCSS` with optimization and fingerprinting
- **Stats Generation**: Automatic via `hugo_stats.json` for CSS purging
- **Module Mounts**: Assets directory mounted for Hugo processing

## Development Workflow

1. Create/edit content in `content/`
2. Install dependencies: `npm install` (first-time setup)
3. Run `hugo server -D` for development with live reload
4. Test changes locally at `localhost:1313`
5. Use `hugo --minify` for production builds
6. Deploy `public/` directory to web server

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
<a href="/categories/{{ . }}/" class="text-red-600 hover:text-red-700">{{ . }}</a>
{{ end }}
```

### Custom Utilities (assets/css/styles.css)
```css
@import 'tailwindcss';

@theme {
  --font-sans: 'Helvetica', system-ui, sans-serif;
  --font-serif: 'Georgia', serif;
}

@utility measure {
  max-width: 30em;
}

@utility nested-links {
  & a {
    @apply text-blue-600 underline;
  }
  & a:hover {
    @apply text-blue-800;
  }
}

@layer base {
  a:link {
    @apply text-red-600 no-underline;
  }
  
  a:visited {
    @apply text-red-600 no-underline;
  }
  
  a:hover {
    @apply text-red-700 underline;
  }
}
```

## Testing Strategy
- **Visual Testing**: `hugo server -D` with browser validation
- **Responsive Testing**: Use browser dev tools for breakpoint testing
- **CSS Validation**: Check Tailwind compilation and custom utility generation
- **RSS Feed Testing**: Verify feed generation and accessibility
- **Link Testing**: Confirm internal links resolve correctly

## Performance Considerations
- **CSS Pipeline**: Hugo processes Tailwind CSS with purging (only used classes included)
- **Production Optimization**: Automatic minification and fingerprinting
- **Bundle Size**: Generated CSS is ~15KB (much smaller than CDN alternatives)
- **Asset Caching**: Hugo's build cache busting via configuration
- **CDN vs Local**: Tailwind CSS is processed and bundled locally

## Migration Notes

### From Tachyons to Tailwind CSS v4 (Completed January 2026)
- **Framework Migration**: Replaced Tachyons 4.12.0 CDN with Tailwind CSS v4.0.5
- **Build Integration**: Hugo's native `css.TailwindCSS` function processing
- **Visual Fidelity**: Maintained Helvetica/Georgia fonts and red accent colors
- **Responsive Design**: Adopted Tailwind's breakpoint system (sm:, md:, lg:, xl:)
- **Performance**: Improved bundle size and build times

### Key Benefits
- **Modern CSS Pipeline**: Integrated processing, purging, and optimization
- **Consistent Styling**: Utility-first approach with custom utilities
- **Better Performance**: Smaller CSS bundles with automatic purging
- **Future-Proof**: Latest Tailwind CSS v4 with ongoing updates