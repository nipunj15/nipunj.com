# nipunj.com

Personal website for Nipun Jain. Built with Jekyll (based on the Long Haul theme), deployed to GitHub Pages.

**Live at [nipunj.com](https://nipunj.com)**

## Local Development

```bash
# Requires Homebrew Ruby (not macOS system Ruby)
export PATH="/opt/homebrew/opt/ruby/bin:/opt/homebrew/lib/ruby/gems/4.0.0/bin:$PATH"
bundle install
bundle exec jekyll serve -w
# Site at http://localhost:4000
```

## Deployment

Pushing to `main` auto-deploys via GitHub Actions.
