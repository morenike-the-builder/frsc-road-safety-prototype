# Deployment Guide

## GitHub ✅

The project is live on GitHub:

**Repository**: https://github.com/morenike-the-builder/frsc-road-safety-prototype

All code is version-controlled and ready for collaboration.

```bash
git clone https://github.com/morenike-the-builder/frsc-road-safety-prototype.git
cd frsc-road-safety-prototype
```

## Vercel Deployment

### Option 1: Auto-Deploy (Recommended)

1. Go to [vercel.com](https://vercel.com)
2. Sign in with GitHub
3. Click "New Project"
4. Select "morenike-the-builder" from the dropdown
5. Search for and select `frsc-road-safety-prototype`
6. Click "Import"
7. Leave default settings and click "Deploy"

The site will deploy automatically and provide a URL like:
```
https://frsc-road-safety-prototype.vercel.app
```

### Option 2: Manual Deployment

1. Install Vercel CLI:
   ```bash
   npm install -g vercel
   ```

2. Deploy from this directory:
   ```bash
   vercel --prod
   ```

## CI/CD

After deployment, every push to GitHub's `main` branch will automatically redeploy on Vercel.

## Local Development

To test locally before pushing:

```bash
python -m http.server 8000
# or
npm run dev
```

Open `http://localhost:8000` in your browser.

## Environment

- **Framework**: Static HTML/CSS/JavaScript
- **No build step required**
- **No external dependencies**
- **Single-page application**

## Vercel Settings (if needed)

If you need to configure custom domains or environment variables:

1. Go to Vercel Dashboard
2. Select the `frsc-road-safety-prototype` project
3. Go to "Settings"
4. Configure as needed

---

**Status**: Ready for production deployment ✅
