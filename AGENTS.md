# AGENTS.md

This file contains comprehensive project-specific instructions for AI assistants working on this codebase.

## Project Overview
This is a **Tailwind Next.js Starter Blog** (v2.4.0) - a feature-rich blogging template built with modern web technologies:

### Core Technologies
- **Next.js 15.2.4** - Using App Router architecture
- **React 19.0.0** - Latest React version
- **TypeScript** - For type safety (with some JS files)
- **Tailwind CSS v4** - Utility-first CSS framework
- **Contentlayer2** - Type-safe content management for MDX files
- **MDX** - Markdown with JSX support for rich content
- **Pliny 0.4.1** - Blog utilities and plugins

### Key Features
- Static site generation with dynamic routing
- MDX blog posts with frontmatter
- Multiple author support
- Tag-based categorization
- Full-text search (Kbar)
- Newsletter integration (multiple providers)
- Comments system (Giscus/Utterances/Disqus)
- Analytics support (Umami/Plausible/GA/etc)
- Dark mode support
- SEO optimized with sitemap and RSS
- Math equation support (KaTeX)
- Code syntax highlighting (Prism)
- Image optimization

## Development Commands

```bash
# Package Manager: Yarn 3.6.1 (Berry)

# Install dependencies
yarn install

# Development server (http://localhost:3000)
yarn dev
# or
yarn start

# Production build
yarn build

# Serve production build
yarn serve

# Linting (auto-fix enabled)
yarn lint

# Bundle analysis
yarn analyze

# Note: No built-in test or typecheck commands
# TypeScript checking happens during build
```

## Project Structure

```
tailwind-nextjs-starter-blog/
├── app/                    # Next.js App Router
│   ├── api/               # API routes
│   │   └── newsletter/    # Newsletter subscription endpoint
│   ├── about/             # About page
│   ├── blog/              # Blog posts and pagination
│   │   ├── [...slug]/     # Individual blog post pages
│   │   └── page/[page]/   # Blog pagination
│   ├── projects/          # Projects showcase page
│   ├── tags/              # Tag pages and pagination
│   ├── layout.tsx         # Root layout
│   ├── page.tsx           # Home page
│   ├── not-found.tsx      # 404 page
│   ├── theme-providers.tsx # Theme context
│   └── tag-data.json      # Generated tag counts
├── components/            # React components
│   ├── social-icons/      # Social media icons
│   ├── Card.tsx           # Blog post card
│   ├── Comments.tsx       # Comments integration
│   ├── Footer.tsx         # Site footer
│   ├── Header.tsx         # Site header/navigation
│   ├── MDXComponents.tsx  # Custom MDX components
│   ├── SearchButton.tsx   # Search functionality
│   └── ThemeSwitch.tsx    # Dark mode toggle
├── css/                   # Styles
│   ├── tailwind.css       # Tailwind imports
│   └── prism.css          # Code highlighting
├── data/                  # Content and configuration
│   ├── authors/           # Author profiles (MDX)
│   ├── blog/              # Blog posts (MDX)
│   ├── headerNavLinks.ts  # Navigation links
│   ├── projectsData.ts    # Projects data
│   └── siteMetadata.js    # Site configuration
├── layouts/               # Page layouts
│   ├── AuthorLayout.tsx   # Author page layout
│   ├── ListLayout.tsx     # Blog list layout
│   ├── PostLayout.tsx     # Blog post layout
│   └── PostSimple.tsx     # Simple post layout
├── public/                # Static assets
│   └── static/
│       ├── favicons/      # Favicon files
│       └── images/        # Blog images
├── scripts/               # Build scripts
│   ├── postbuild.mjs      # Post-build tasks
│   └── rss.mjs            # RSS feed generation
└── Configuration Files
    ├── contentlayer.config.ts  # Content processing
    ├── next.config.js          # Next.js config
    ├── tailwind.config.js      # Tailwind config (if exists)
    ├── postcss.config.js       # PostCSS config
    ├── tsconfig.json           # TypeScript config
    ├── eslint.config.mjs       # ESLint config
    ├── prettier.config.js      # Prettier config
    └── .env.example            # Environment variables template
```

## Code Style and Conventions

### TypeScript Configuration
- Target: ES6
- Module: ESNext with bundler resolution
- Strict mode: Partially enabled (strictNullChecks only)
- Path aliases configured:
  - `@/components/*` → `components/*`
  - `@/data/*` → `data/*`
  - `@/layouts/*` → `layouts/*`
  - `@/css/*` → `css/*`

### Code Formatting (Prettier)
- **No semicolons** (semi: false)
- **Single quotes** for strings
- Print width: 100 characters
- Tab width: 2 spaces
- Trailing comma: ES5
- Bracket spacing: true
- Tailwind CSS class sorting enabled

### Linting Rules (ESLint)
- Extends: Next.js, TypeScript recommended, JSX a11y, Prettier
- React in scope not required
- Unused variables allowed
- Unescaped entities allowed
- Explicit module boundaries not required

### Component Guidelines
1. Use TypeScript for new components (`.tsx` extension)
2. Follow existing patterns in `/components` directory
3. Use Tailwind CSS classes for styling
4. Implement responsive design
5. Support dark mode where applicable
6. Keep components focused and reusable
7. Use semantic HTML elements
8. Follow accessibility best practices

### Content Management
- Blog posts in `/data/blog/` as MDX files
- Frontmatter fields:
  - `title` (required)
  - `date` (required)
  - `tags` (array)
  - `draft` (boolean)
  - `summary`
  - `images` (array)
  - `authors` (array)
  - `layout`
  - `canonicalUrl`
- Author profiles in `/data/authors/` as MDX files
- Nested routing supported for multi-part posts

## Environment Variables

Create a `.env.local` file based on `.env.example`:

```bash
# Comments System (choose one)
NEXT_PUBLIC_GISCUS_REPO=
NEXT_PUBLIC_GISCUS_REPOSITORY_ID=
NEXT_PUBLIC_GISCUS_CATEGORY=
NEXT_PUBLIC_GISCUS_CATEGORY_ID=
NEXT_PUBLIC_UTTERANCES_REPO=
NEXT_PUBLIC_DISQUS_SHORTNAME=

# Newsletter Providers (choose one)
MAILCHIMP_API_KEY=
MAILCHIMP_API_SERVER=
MAILCHIMP_AUDIENCE_ID=

BUTTONDOWN_API_KEY=

CONVERTKIT_API_KEY=
CONVERTKIT_FORM_ID=

KLAVIYO_API_KEY=
KLAVIYO_LIST_ID=

REVUE_API_KEY=

EMAILOCTOPUS_API_KEY=
EMAILOCTOPUS_LIST_ID=

BEEHIIV_API_KEY=
BEEHIIV_PUBLICATION_ID=

# Analytics (optional)
NEXT_UMAMI_ID=
```

## Git Workflow

### Pre-commit Hooks
- Husky configured with lint-staged
- Automatically runs on staged files:
  - ESLint with auto-fix for `.js`, `.jsx`, `.ts`, `.tsx`
  - Prettier formatting for all supported files

### Commit Guidelines
1. Write clear, descriptive commit messages
2. Test changes locally before committing
3. Ensure no linting errors
4. Verify build succeeds
5. Follow conventional commit format when applicable

### Before Committing
```bash
# Run linting
yarn lint

# Test build
yarn build

# Manual format check (if needed)
npx prettier --check .
```

## Security Configuration

The project implements strict security headers:
- Content Security Policy (CSP)
- Referrer Policy: strict-origin-when-cross-origin
- X-Frame-Options: DENY
- X-Content-Type-Options: nosniff
- Strict-Transport-Security enabled
- Permissions Policy restricting camera, microphone, geolocation

## API Routes

### Newsletter Subscription
- Endpoint: `/api/newsletter`
- Method: POST
- Supports multiple providers (configured via environment variables)

## Deployment Considerations

1. **Static Export**: Supports static export with `EXPORT=true`
2. **Base Path**: Configurable via `BASE_PATH` environment variable
3. **Image Optimization**: Can be disabled with `UNOPTIMIZED=true`
4. **Bundle Analysis**: Available with `yarn analyze`
5. **GitHub Pages**: Workflow configured in `.github/workflows/pages.yml`

## Common Tasks

### Adding a New Blog Post
1. Create MDX file in `/data/blog/`
2. Add required frontmatter
3. Write content using Markdown/MDX
4. Images go in `/public/static/images/`
5. Run dev server to preview

### Adding an Author
1. Create MDX file in `/data/authors/`
2. Include author metadata
3. Reference in blog post frontmatter

### Customizing Site Metadata
Edit `/data/siteMetadata.js` for:
- Site title, description, URL
- Social media links
- Analytics configuration
- Comment system settings
- Newsletter provider

### Modifying Navigation
Edit `/data/headerNavLinks.ts` to add/remove navigation items

## Performance Optimization

- Automatic image optimization with Next.js Image
- Static generation for all pages
- Code splitting and lazy loading
- Minified production builds
- Rehype plugins for content optimization
- Bundle analysis available

## Troubleshooting

### Common Issues
1. **Build failures**: Check for TypeScript errors and missing environment variables
2. **Styling issues**: Ensure Tailwind classes are not purged
3. **Content not updating**: Clear `.contentlayer` cache
4. **Search not working**: Verify search index generation in build

### Debug Commands
```bash
# Clean build
rm -rf .next .contentlayer node_modules/.cache
yarn build

# Check for TypeScript errors
npx tsc --noEmit

# Analyze bundle size
yarn analyze
```

## Additional Resources

- [Next.js Documentation](https://nextjs.org/docs)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [Contentlayer Documentation](https://contentlayer.dev)
- [MDX Documentation](https://mdxjs.com)
- [Pliny Documentation](https://github.com/timlrx/pliny)