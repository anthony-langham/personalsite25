# Personal Site 2025

My personal website and blog built with Next.js, Tailwind CSS, and MDX.

## Tech Stack

- **Framework**: [Next.js 15.2.4](https://nextjs.org/) (App Router)
- **Styling**: [Tailwind CSS v4](https://tailwindcss.com/)
- **Content**: [MDX](https://mdxjs.com/) with [Contentlayer2](https://contentlayer.dev/)
- **Deployment**: [Vercel](https://vercel.com)

## Features

- ✨ Static site generation with dynamic routing
- 📝 MDX blog posts with rich content support
- 🏷️ Tag-based categorization
- 🔍 Full-text search
- 🌙 Dark mode support
- 📱 Fully responsive design
- 🚀 SEO optimized with sitemap and RSS
- 💬 Comments system (Giscus)
- 📊 Analytics support
- 🔢 Math equations (KaTeX)
- 🎨 Syntax highlighting (Prism)

## Getting Started

### Prerequisites

- Node.js 18+ 
- Yarn 3.6.1

### Installation

```bash
# Clone the repository
git clone https://github.com/anthony-langham/personalsite25.git
cd personalsite25

# Install dependencies
yarn install

# Create environment variables
cp .env.example .env.local
# Edit .env.local with your configuration
```

### Development

```bash
# Start development server
yarn dev

# Build for production
yarn build

# Run production server
yarn serve

# Lint code
yarn lint
```

## Project Structure

```
├── app/                    # Next.js App Router pages
├── components/            # React components
├── data/                  # Content and configuration
│   ├── authors/          # Author profiles (MDX)
│   ├── blog/             # Blog posts (MDX)
│   └── siteMetadata.js   # Site configuration
├── layouts/              # Page layouts
├── public/               # Static assets
└── css/                  # Styles
```

## Configuration

### Site Metadata

Edit `data/siteMetadata.js` to customize:
- Site title, description, and URL
- Social media links
- Analytics and comment system settings
- Newsletter provider

### Navigation

Edit `data/headerNavLinks.ts` to modify navigation links.

### Content

- **Blog posts**: Add MDX files to `data/blog/`
- **Authors**: Add author profiles to `data/authors/`
- **Projects**: Edit `data/projectsData.ts`

## Writing Blog Posts

Create a new `.mdx` file in `data/blog/` with frontmatter:

```mdx
---
title: 'My Blog Post Title'
date: '2025-01-18'
tags: ['nextjs', 'react']
draft: false
summary: 'A brief description of the post'
---

Your content here...
```

## Deployment

The site is configured for easy deployment on Vercel:

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel
```

## Development Guidelines

For detailed development guidelines, code style conventions, and troubleshooting, see [AGENTS.md](./AGENTS.md).

## License

This project is based on the [Tailwind Nextjs Starter Blog](https://github.com/timlrx/tailwind-nextjs-starter-blog) template.

---

Built with ❤️ using Next.js and Tailwind CSS