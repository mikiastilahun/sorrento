# Deployment Guide

## Deploy to Vercel (Recommended)

This project is optimized for deployment on Vercel.

### Option 1: Deploy via Vercel CLI

1. **Install Vercel CLI:**

```bash
pnpm add -g vercel
```

2. **Login to Vercel:**

```bash
vercel login
```

3. **Deploy:**

```bash
vercel
```

4. **Deploy to Production:**

```bash
vercel --prod
```

### Option 2: Deploy via Vercel Dashboard

1. **Push your code to GitHub:**

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin YOUR_GITHUB_REPO_URL
git push -u origin main
```

2. **Import to Vercel:**
   - Go to [vercel.com](https://vercel.com)
   - Click "Add New Project"
   - Import your GitHub repository
   - Vercel will automatically detect SvelteKit and configure everything

3. **Configure Build Settings:**
   - Framework Preset: SvelteKit
   - Build Command: `pnpm run build`
   - Output Directory: `.svelte-kit` (auto-detected)
   - Install Command: `pnpm install`

### Environment Variables

If you need environment variables:

1. Go to your Vercel project settings
2. Navigate to "Environment Variables"
3. Add your variables (they should start with `PUBLIC_` if you want them available in the browser)

## Build Locally

To test the production build locally:

```bash
pnpm run build
pnpm run preview
```

## Project Configuration

- **Framework:** SvelteKit 2
- **Adapter:** @sveltejs/adapter-vercel
- **Node Runtime:** 20.x
- **Package Manager:** pnpm
- **Build Output:** Vercel Edge Functions

## Features

- ✅ Internationalization (i18n) with Paraglide
- ✅ MDSveX for markdown content
- ✅ Tailwind CSS v4
- ✅ Full TypeScript support
- ✅ SEO optimized
- ✅ Responsive design
- ✅ Modern UI components

## Performance

The site is optimized for:

- Fast initial page load
- Image optimization
- Code splitting
- Server-side rendering (SSR)
- Static generation where possible

## Support

For issues or questions, please check the project repository or contact the development team.

