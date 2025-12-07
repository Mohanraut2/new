# Vercel Deployment Guide for AJ247 Studios

## Overview
This static website is optimized for Vercel's static site hosting. All configuration is already in place.

## Pre-Deployment Checklist

- ✅ All HTML files are in the root directory
- ✅ CSS and JS files are properly linked in subdirectories
- ✅ 404.html error page is configured
- ✅ vercel.json configuration is set
- ✅ .vercelignore file excludes unnecessary files

## Deployment Steps

### Option 1: Using Vercel CLI
```bash
# Install Vercel CLI
npm install -g vercel

# Deploy from project root
vercel
```

### Option 2: GitHub Integration (Recommended)
1. Push your code to GitHub
2. Go to [vercel.com](https://vercel.com/dashboard)
3. Click "New Project"
4. Select your GitHub repository
5. Click "Deploy"

Vercel will automatically detect this as a static site and deploy without any build steps.

## Configuration Explained

### vercel.json
- **framework**: "static" – Tells Vercel this is a static site with no build step
- **cleanUrls**: true – Serves `/page` instead of `/page.html`
- **trailingSlash**: false – URLs don't end with `/`
- **headers**: Adds security and caching headers
  - Cache-Control: 1-hour caching for performance
  - X-Content-Type-Options: Prevents MIME-type sniffing
  - X-Frame-Options: Protects against clickjacking

### .vercelignore
Excludes files that don't need to be deployed:
- Git files (.git, .gitignore)
- Development files (node_modules, IDE settings)
- Environment files

## Performance Optimization

### Already Configured
✅ Images cached for 1 hour  
✅ CSS/JS cached for 1 hour  
✅ HTML pages cached for 1 hour (can be adjusted)  

### Recommendations
- Consider lazy-loading images in album pages
- Minify CSS/JS files for faster loading
- Optimize image file sizes (JPG/WebP format)

## Custom Domain Setup

1. In Vercel Dashboard → Project Settings → Domains
2. Add your custom domain (e.g., aj247studios.com)
3. Update DNS records at your domain provider:
   - Point to: `cname.vercel.com`
   - Or use Vercel's nameservers for easier management

## Environment Variables
Currently none needed. All content is public.

## Troubleshooting

### 404 Error on Reloads
- ✅ Fixed by `vercel.json` rewrite rules
- Clean URLs work automatically

### Images Not Loading
- Check relative paths in HTML (should use `other-img/`, `sports/`, etc.)
- Verify image files exist in deployment

### Performance Issues
- Use Vercel Analytics to monitor
- Check file sizes in Network tab
- Consider CDN for large media files

## Analytics & Monitoring

Enable in Vercel Dashboard:
1. Project Settings → Analytics
2. Monitor page performance and user metrics
3. Set performance budgets

## Next Steps

1. **Domain**: Update `vercel.json` with your production domain
2. **Analytics**: Enable Vercel Web Analytics or Google Analytics
3. **Monitoring**: Set up error alerts in Vercel Dashboard
4. **CI/CD**: Vercel auto-deploys on every push to main branch

## Support

- Vercel Docs: https://vercel.com/docs
- Vercel Community: https://github.com/vercel/vercel/discussions
