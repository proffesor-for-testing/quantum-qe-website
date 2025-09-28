# Quantum QE Website - Cloudflare Pages Deployment Guide

## Quick Start

This website is ready to deploy on Cloudflare Pages. Follow these steps to get your site live on quantum-qe.dev.

## Prerequisites

1. **Domain Setup**: Ensure quantum-qe.dev is registered and pointed to Cloudflare's nameservers
2. **Cloudflare Account**: Sign up at https://cloudflare.com if you haven't already
3. **GitHub Account**: For easier deployment (optional but recommended)

## Deployment Options

### Option 1: Direct Upload (Quickest)

1. **Prepare Files**:
   - Ensure you have `index.html` and `favicon.svg` in a folder
   - No build process needed - this is a static site

2. **Deploy to Cloudflare Pages**:
   - Go to [Cloudflare Dashboard](https://dash.cloudflare.com/)
   - Navigate to "Workers & Pages" → "Create application" → "Pages"
   - Select "Upload assets"
   - Name your project: `quantum-qe`
   - Drag and drop your folder or select files
   - Click "Deploy site"

3. **Connect Custom Domain**:
   - After deployment, go to your Pages project
   - Click "Custom domains" tab
   - Add `quantum-qe.dev` and `www.quantum-qe.dev`
   - Follow the DNS configuration instructions

### Option 2: GitHub Integration (Recommended for Updates)

1. **Create GitHub Repository**:
   ```bash
   # Create new repo on GitHub named 'quantum-qe-website'
   git init
   git add index.html favicon.svg
   git commit -m "Initial commit - Quantum QE website"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/quantum-qe-website.git
   git push -u origin main
   ```

2. **Connect to Cloudflare Pages**:
   - Go to Cloudflare Dashboard → "Workers & Pages"
   - Click "Create application" → "Pages" → "Connect to Git"
   - Authorize GitHub and select your repository
   - Configuration settings:
     - Project name: `quantum-qe`
     - Production branch: `main`
     - Build command: (leave empty)
     - Build output directory: `/`
   - Click "Save and Deploy"

3. **Automatic Deployments**:
   - Every push to `main` will automatically deploy
   - Preview deployments for other branches

## DNS Configuration

If your domain isn't automatically configured:

1. Go to your Cloudflare DNS settings
2. Add these records (Cloudflare will usually do this automatically):
   ```
   Type: CNAME
   Name: quantum-qe.dev
   Content: quantum-qe.pages.dev
   Proxy: On (orange cloud)
   
   Type: CNAME  
   Name: www
   Content: quantum-qe.pages.dev
   Proxy: On (orange cloud)
   ```

## Performance Optimization

Cloudflare Pages automatically provides:
- ✅ Global CDN distribution
- ✅ SSL/HTTPS certificates
- ✅ HTTP/2 and HTTP/3 support
- ✅ Brotli compression
- ✅ Cache headers optimization

### Additional Optimizations (Optional)

1. **Page Rules** (if on paid plan):
   - Cache Level: Cache Everything
   - Edge Cache TTL: 1 month

2. **Speed Settings**:
   - Enable Auto Minify (HTML, CSS, JavaScript)
   - Enable Rocket Loader (if no conflicts)
   - Enable Mirage (for images)

## Monitoring & Analytics

1. **Enable Web Analytics**:
   - Go to your Pages project
   - Click "Analytics" tab
   - Enable Web Analytics (privacy-friendly, no cookies)

2. **Set up Real User Monitoring** (optional):
   - Available in paid Cloudflare plans
   - Provides Core Web Vitals data

## Future Enhancements

### Add these files as you expand:

1. **robots.txt**:
```txt
User-agent: *
Allow: /
Sitemap: https://quantum-qe.dev/sitemap.xml
```

2. **sitemap.xml**:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://quantum-qe.dev/</loc>
    <lastmod>2025-09-01</lastmod>
    <priority>1.0</priority>
  </url>
</urlset>
```

3. **_headers** (for security headers):
```
/*
  X-Frame-Options: DENY
  X-Content-Type-Options: nosniff
  Referrer-Policy: strict-origin-when-cross-origin
  Permissions-Policy: accelerometer=(), camera=(), geolocation=(), gyroscope=(), magnetometer=(), microphone=(), payment=(), usb=()
```

## Multi-Language Support (Future)

When ready to add Serbian language support:

1. Create `/sr/index.html` for Serbian version
2. Add language selector to navigation
3. Configure URL structure:
   - English: `quantum-qe.dev`
   - Serbian: `quantum-qe.dev/sr`

## Testing Before Launch

1. **Check Responsiveness**:
   - Test on mobile, tablet, desktop
   - Use Chrome DevTools device emulation

2. **Performance Testing**:
   - Run [PageSpeed Insights](https://pagespeed.web.dev/)
   - Target 90+ scores on all metrics

3. **SEO Check**:
   - Verify meta tags are present
   - Check Open Graph tags with [Facebook Debugger](https://developers.facebook.com/tools/debug/)
   - Test with [LinkedIn Post Inspector](https://www.linkedin.com/post-inspector/)

## Go-Live Checklist

- [ ] Domain DNS properly configured
- [ ] SSL certificate active (automatic with Cloudflare)
- [ ] Website loads on quantum-qe.dev
- [ ] Website loads on www.quantum-qe.dev
- [ ] Mobile responsive design working
- [ ] Contact email (dragan@quantum-qe.dev) is active
- [ ] Analytics enabled
- [ ] Social media meta tags working
- [ ] All links tested and working

## Support

- **Cloudflare Pages Docs**: https://developers.cloudflare.com/pages/
- **Cloudflare Community**: https://community.cloudflare.com/
- **Status Page**: https://www.cloudflarestatus.com/

## Quick Updates

To update the site after deployment:

### If using Direct Upload:
1. Make changes to files locally
2. Go to Cloudflare Pages dashboard
3. Click "Create deployment"
4. Upload new files

### If using GitHub:
```bash
git add .
git commit -m "Update: description of changes"
git push origin main
```
Site updates automatically in ~1 minute.

---

## Notes

- The website is optimized for Core Web Vitals out of the box
- No build process needed - pure HTML/CSS/JS
- Cloudflare Pages free tier includes:
  - 500 deployments per month
  - Unlimited bandwidth
  - Unlimited requests
  
Perfect for your consulting website needs!
