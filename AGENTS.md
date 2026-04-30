# AGENTS.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Development commands
- Install dependencies: `npm install`
- Start local dev server: `npm start` (runs `astro dev`, default: http://localhost:4321)
- Production build: `npm run build` (outputs static site to `dist/`)

## Linting and tests
- No lint script is currently defined in `package.json`.
- No test script/framework is currently configured in this repository.
- Because tests are not configured, there is no single-test command yet.

## High-level architecture
- This is a static Astro blog using MDX content and Astro content collections.
- Core site config is in `astro.config.mjs`:
  - MDX support via `@astrojs/mdx`
  - Sitemap generation via `@astrojs/sitemap`
  - `site` URL is required for canonical URLs and sitemap correctness.
- Shared page shell is `src/layouts/Base.astro`:
  - Global neon/dark styling, navigation, SEO meta tags, canonical link generation.
  - All top-level pages and blog routes render through this layout.

## Content model and routing flow
- Blog content source is `src/content/blog/*.mdx`.
- Content schema is centralized in `src/content.config.ts` (title, description, pubDate, tags).
- Main route behavior:
  - `src/pages/index.astro`: fetches `blog` collection and shows latest 5 posts.
  - `src/pages/blog/index.astro`: full post listing sorted by `pubDate` descending.
  - `src/pages/blog/[slug].astro`: static paths generated from content IDs; renders MDX with `render(post)`.
  - `src/pages/tags/[tag].astro`: static tag pages generated from unique tags across all posts.
  - `src/pages/search.astro`: client-side search over serialized post metadata (title/description/tags).

## Known configuration placeholders
- `astro.config.mjs` still uses placeholder `site: 'https://your-blog-url.com'`.
- Giscus comment settings in `src/pages/blog/[slug].astro` are placeholder values (`data-repo`, IDs, etc.) and must be replaced for real comments.
