# GNNL TV

A modern website built with [Astro](https://astro.build/) featuring a Twitch stream embed, blog posts, and simple content pages.

## Features

- **Homepage** with configurable Twitch embed and editable copy
- **Blog Archive** displaying posts from two different blog types
- **Shared Blog Post Template** for both blog types
- **Simple Page Template** for static content pages
- **Minimal styling** with CSS files ready for customization
- **GitHub Actions** for automated builds and deployment

## Project Structure

```
/
├── public/
│   ├── favicon.svg
│   └── styles/
│       └── global.css          # Global styles
├── src/
│   ├── content/
│   │   ├── config.ts           # Content collections config
│   │   ├── manifesto/          # Manifesto posts
│   │   └── blog-type-2/        # Blog type 2 posts
│   ├── layouts/
│   │   ├── BaseLayout.astro    # Main layout
│   │   └── BlogPostLayout.astro # Blog post layout
│   └── pages/
│       ├── index.astro         # Homepage with Twitch embed
│       ├── about.astro         # Simple page example
│       └── blog/
│           ├── index.astro     # Blog archive
│           └── [slug].astro    # Dynamic blog post pages
├── astro.config.mjs            # Astro configuration
├── package.json
└── tsconfig.json
```

## Getting Started

### Prerequisites

- Node.js 18 or higher
- npm or yarn

### Installation

```bash
npm install
```

### Development

Start the development server:

```bash
npm run dev
```

The site will be available at `http://localhost:4321`

### Building for Production

```bash
npm run build
```

The built site will be in the `dist/` directory.

### Preview Production Build

```bash
npm run preview
```

## Configuration

### Twitch Embed

To configure the Twitch embed on the homepage:

1. Open `src/pages/index.astro`
2. Update the `twitchChannel` variable with your Twitch channel name
3. Update the `twitchParent` variable with your domain (use your actual domain in production)

### Adding Blog Posts

#### Manifesto

Create a new markdown file in `src/content/manifesto/`:

```markdown
---
title: "Your Post Title"
description: "Post description"
pubDate: 2024-01-15
author: "Your Name"
tags: ["tag1", "tag2"]
---

Your content here...
```

#### Blog Type 2

Create a new markdown file in `src/content/blog-type-2/` with the same format.

Both blog types will appear together in the blog archive at `/blog`.

### Creating Simple Pages

To create a new simple page:

1. Create a new `.astro` file in `src/pages/` (e.g., `contact.astro`)
2. Use the `BaseLayout` component
3. Add your content

Example:

```astro
---
import BaseLayout from '../layouts/BaseLayout.astro';
---

<BaseLayout title="Contact" description="Contact us">
  <div class="simple-page">
    <h1>Contact</h1>
    <p>Your content here...</p>
  </div>
</BaseLayout>
```

## Styling

The site includes minimal base styling in `public/styles/global.css`. This provides:

- Basic reset and typography
- Header and footer styles
- Blog post styles
- Responsive design breakpoints

You can extend or customize these styles as needed.

## GitHub Actions

The repository includes a GitHub Actions workflow (`.github/workflows/deploy.yml`) that:

- Runs on push to `main` branch or pull requests
- Builds the site
- Deploys to GitHub Pages (on main branch only)

To use GitHub Pages deployment, enable GitHub Pages in your repository settings and select "GitHub Actions" as the source.

## Learn More

- [Astro Documentation](https://docs.astro.build)
- [Astro Discord](https://astro.build/chat)

## License

ISC