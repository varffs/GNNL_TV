# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev      # Start dev server at localhost:4321
npm run build    # Type-check with astro check, then build to dist/
npm run preview  # Preview production build locally
```

## Architecture

This is an Astro 5 static site with three content collections and Stylus for CSS preprocessing.

### Content Collections (`src/content/config.ts`)

- **manifesto** - Blog posts displayed inline on `/manifesto` (full content rendered on archive page)
- **communiques** - Blog posts with individual pages at `/communiques/[slug]`
- **pages** - Static content pages (currently `san` and `chat`) rendered via `src/pages/[page].astro`

All blog posts use the same schema: `title`, `description`, `pubDate`. Pages use: `title`, `description`.

### Layouts

- `BaseLayout.astro` - Main wrapper with navigation (can be hidden via `hideNavigation` prop)
- `BlogPostLayout.astro` - Individual blog post display

### Routing

- `/` - Homepage with Twitch embed (navigation hidden)
- `/manifesto` - Single-page manifesto archive showing full post content inline
- `/communiques` - Archive listing with links to individual posts
- `/communiques/[slug]` - Individual communique posts
- `/san`, `/chat` - Dynamic pages from `pages` collection via `[page].astro`

### Styling

Uses Stylus (`src/styles/global.styl`) imported in BaseLayout. Key CSS classes:
- `.homepage`, `.blog-archive`, `.blog-post`, `.simple-page` - Page-type containers

## Deployment

GitHub Actions deploys to GitHub Pages on push to `main`. Site domain: `gnnl_tv.patrickbest.com`

## Configuration

Twitch embed settings are at the top of `src/pages/index.astro` (twitchChannel, twitchParent).
