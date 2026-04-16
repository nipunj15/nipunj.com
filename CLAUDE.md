# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

```bash
# Install dependencies (requires Homebrew Ruby, not system Ruby 2.6)
export PATH="/opt/homebrew/opt/ruby/bin:/opt/homebrew/lib/ruby/gems/4.0.0/bin:$PATH"
bundle install

# Serve locally with watch
bundle exec jekyll serve -w
# Site at http://localhost:4000

# Production build
bundle exec jekyll build
```

Pushing to `main` auto-deploys to https://nipunj.com via GitHub Actions (`.github/workflows/deploy.yml`).

## Architecture

This is a personal website built on the **Long Haul** Jekyll theme, heavily customized.

### Content Structure
- `index.html` — Landing page (About content, not a blog feed)
- `work.md` — Professional timeline with custom CSS timeline component
- `projects.md`, `thesis.md` — Static pages
- `_posts/` — Blog posts (exist but no dedicated listing page currently)

### Color/Design System (`_sass/_config.scss`)
The palette was deliberately chosen for cohesion — don't introduce colors that break the warm, unified feel:
- **Header**: seagreen background + gold (#FFD700) text
- **Body**: cream (#FAF8F5) background + dark forest green (#1B4332) text
- **Links**: #2E7D52 (dark green)
- **Accents**: #FFD700 (yellow) used for page title underlines, timeline dots, blockquote decorations, drop caps, post separators, footer border

### SASS Structure
`assets/css/style.scss` is the entry point. Import order matters:
1. normalize → config → partials → modules → breakpoints → custom
2. Three responsive breakpoints: mobile-first (610px container), 800px+ (880px), 1200px+ (990px)
3. Dark mode via `prefers-color-scheme: dark` media queries in both `_mobileup.scss` and `_800up.scss`
4. Custom styles go in `_sass/custom/` (currently has `_timeline.scss`)

### Templates
- `_layouts/default.html` — Main wrapper (head, header, content, footer, scripts)
- `_layouts/post.html` — Blog post with prev/next navigation
- `_includes/header.html` — Nav bar, reads from `site.navigation` in config
- `_includes/footer.html` — Social icons, reads from `site.social` in config
- `_includes/footer_links/` — SVG social icons (uses X icon, not Twitter)

### Key Config (`_config.yml`)
- Navigation menu and social links are defined here
- `brief.md` is excluded from builds (private planning doc, also in .gitignore)
- No Google Analytics or Disqus enabled

### JavaScript
- `dropcap.min.js` — Drop caps on posts (requires `<span class="dropcap">` markup)
- `responsive-nav.min.js` — Mobile hamburger menu toggle
- jQuery 1.11.2 for reading time rounding
