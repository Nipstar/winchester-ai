# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Winchester AI Services** — A satellite SEO site for AI automation services targeting Winchester, Hampshire. Part of a Hampshire-wide network of local satellite sites (Andover, Portsmouth, Southampton, Basingstoke, Farnborough) all powered by Antek Automation.

**Domain:** aiserviceswinchester.co.uk
**Parent Brand:** Antek Automation (antekautomation.com)
**Tech Stack:** Static HTML (no build process, no frameworks, no dependencies)

## Architecture

### Satellite Site System

This is one of 6+ satellite sites targeting different Hampshire cities. Each site:
- Shares the same visual design and structure
- Uses unique, non-duplicate content to avoid SEO penalties
- Links to parent company (Antek Automation) and partner (Retell AI)
- Cross-links to other satellites in the footer
- Has city-specific SEO metadata, structured data, and geo-coordinates
- Uses local landmarks, neighborhoods, and business context in copy

**CRITICAL:** Content must be unique across all satellites. Google penalizes duplicate content. See SATELLITE_BUILD_INSTRUCTIONS.md for detailed content uniqueness requirements.

### File Structure

```
.
├── index.html              # Complete single-page website (all CSS/JS inline)
├── privacy-policy.html     # Privacy policy page
├── terms.html             # Terms and conditions page
├── robots.txt             # Search engine crawl rules
├── sitemap.xml            # XML sitemap for SEO
├── images/
│   └── bolt.webp          # Bolt Electrical case study screenshot
├── SATELLITE_BUILD_INSTRUCTIONS.md  # Comprehensive build guide
├── CLAUDE.md              # This file
└── README.md              # Project documentation
```

### Core Sections in index.html

All content lives in a single HTML file with inline CSS and vanilla JavaScript:

1. **SEO Metadata** (lines 3-100): Title, meta descriptions, OG tags, JSON-LD structured data (LocalBusiness, Organization, FAQPage)
2. **Hero Section**: Animated gradient orb, city-specific headline and copy
3. **Pain Points**: 3 cards addressing business challenges (must use unique wording per city)
4. **Services**: AI Voice Agents, AI Chatbots, Workflow Automation
5. **Demo Section**: Bolt Electrical case study (universal across all sites)
6. **How It Works**: 3-step process (universal)
7. **Industries**: 8 industry cards (universal)
8. **Why Choose Us**: Retell AI Partner status, local card (must be unique per city)
9. **FAQ**: 10+ questions (all answers must be uniquely worded per city)
10. **Contact Form**: Posts to n8n webhook with hidden city/source fields
11. **Cal.com Booking**: Embedded scheduling widget
12. **GEO/AI Statement**: SEO-dense paragraph above footer (must be unique per city)
13. **Footer**: Cross-links to other satellites, Antek Automation and Retell AI links

### Styling & Interactivity

- **CSS**: All inline in `<style>` tags (custom properties, dark premium theme)
- **JavaScript**: Vanilla JS for IntersectionObserver animations, FAQ accordion, smooth scroll, form handling
- **Animations**: Gradient orb (CSS keyframes), fade-in-up on scroll, stat counters
- **Fonts**: Google Fonts (Sora for headings, DM Sans for body)

## Development Workflow

### No Build Commands

This is a static HTML site. There are no build, lint, or test commands. To develop:

1. Open `index.html` in a browser (can use live server in VS Code)
2. Edit HTML/CSS/JS directly in the file
3. Refresh browser to see changes

### Making Content Edits

**Read SATELLITE_BUILD_INSTRUCTIONS.md first** — it contains the complete transformation process for satellite sites.

When editing content:
- **Always preserve Antek Automation references** (parent company, footer links, trust bar)
- **Always preserve Retell AI Partner links** (trust bar, Why Us section, footer)
- **Keep shared phone number**: 0333 038 9960 (universal across all satellites)
- **Update city-specific email**: hello@[domain]
- **Ensure unique wording** for hero subheadline, pain points, services subtitle, FAQ answers, local card, GEO statement

### Variable Replacement System

Sites use placeholder variables during build (see SATELLITE_BUILD_INSTRUCTIONS.md):

- `[CITY]` → "Winchester"
- `[DOMAIN]` → "aiserviceswinchester.co.uk"
- `[BRAND_NAME]` → "Winchester AI Services" (or similar)
- `[EMAIL]` → "hello@aiserviceswinchester.co.uk"
- `[GEO_LAT]` / `[GEO_LNG]` → Winchester coordinates
- `[NEARBY_TOWNS]` → "Eastleigh, Romsey, Stockbridge"
- `[LOCAL_LANDMARKS]` → Specific Winchester locations for natural copy integration
- `[BUSINESS_VIBE]` → Local business context for writing unique copy

**Before deployment:** Verify zero `[BRACKETS]` remain in HTML.

## SEO Requirements

### Critical for Rankings

1. **Unique Content**: Hero subheadline, pain points, services subtitle, FAQ answers, Why Us local card, GEO statement — all must use different wording/structure than other satellites
2. **Geo Targeting**: Meta geo tags, JSON-LD coordinates, local landmarks in copy, nearby towns mentioned 3+ times
3. **Structured Data**: LocalBusiness schema with correct coordinates, FAQPage schema with all questions, Organization schema with parent company reference
4. **Character Limits**: Title <60 chars, meta description <155 chars, OG title ~55 chars, OG description ~130 chars
5. **Internal Linking**: Cross-link to other satellites in footer (exclude current site from list)
6. **External Trust Signals**: Link to antekautomation.com, retellai.com/partner/antek-automation

### Sitemap & Robots

Update `sitemap.xml` with current date when deploying. Format:
```xml
<lastmod>2026-02-15</lastmod>
```

Verify `robots.txt` has correct domain in Sitemap URL.

## Deployment

### Static Hosting

No build step required. Deploy these files to any static host:
- `index.html`
- `privacy-policy.html`
- `terms.html`
- `robots.txt`
- `sitemap.xml`
- `images/` folder

**Recommended Hosts:**
- GitHub Pages (set publish directory to `/`)
- Netlify (publish directory: `/`)
- Vercel (framework preset: Other)

### Git Workflow

When committing changes:
- Use descriptive commit messages referencing what changed (e.g., "Update Winchester FAQ answers for uniqueness")
- Include Co-Authored-By line: `Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>`
- Never commit with `--no-verify` (respect hooks)
- Push to GitHub after commit

Example commit:
```bash
git add index.html
git commit -m "Update Winchester-specific hero copy

- Rewrote hero subheadline with local landmark references
- Made pain points subtitle unique with city context
- All changes maintain SEO character limits

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"
```

## Important Files

### SATELLITE_BUILD_INSTRUCTIONS.md

**Comprehensive guide** for transforming the base Andover site into a new satellite site. Contains:
- Step-by-step transformation process (18 steps)
- Variable reference format
- Content uniqueness checklist
- Quality control checklist
- Post-launch actions

**Read this file** before making major edits or creating new satellite sites.

### index.html

Single-page website containing all HTML, CSS, and JavaScript. Large file (~90KB, ~2500 lines) with:
- Lines 1-100: SEO metadata and structured data
- Lines 100-500: CSS (custom properties, layout, components, animations)
- Lines 500-2300: HTML content (all sections)
- Lines 2300-2500: JavaScript (animations, interactions, form handling)

When editing, use file path references like `index.html:42` to specify line numbers.

## Cross-Site Network

All satellites link to each other in the footer. Current network:
- **Hampshire** (aiserviceshampshire.co.uk) — County-wide hub
- **Andover** (aiautomationandover.co.uk) — Base/original site
- **Portsmouth** (aiautomationportsmouth.co.uk)
- **Southampton** (aiautomationsouthampton.co.uk)
- **Basingstoke** (aiautomationbasingstoke.co.uk)
- **Winchester** (aiserviceswinchester.co.uk) — This site
- **Farnborough** (aiautomationfarnborough.co.uk)

When editing footer cross-links, exclude the current site from the list.

## Contact Form Integration

Form at bottom of index.html posts to n8n webhook. Hidden fields track:
```html
<input type="hidden" name="source" value="aiserviceswinchester.co.uk">
<input type="hidden" name="city" value="Winchester">
```

These fields enable lead tracking by city/source in the backend CRM.

## Common Tasks

**Update FAQ answers for uniqueness:**
1. Read lines 81-300 in index.html (JSON-LD FAQ schema)
2. Read FAQ section in HTML (search for `<section id="faq">`)
3. Rewrite answers using different sentence structure, examples, and phrasing
4. Verify JSON-LD and HTML answers match
5. Test character counts stay reasonable

**Change city-specific copy:**
1. Identify section needing change (hero, pain points, services, etc.)
2. Read surrounding context to understand current wording
3. Rewrite with Winchester-specific landmarks/neighborhoods from SATELLITE_BUILD_INSTRUCTIONS.md variable set
4. Ensure wording differs from other satellites (avoid duplicate content)
5. Check SEO character limits if editing meta tags

**Update coordinates:**
1. Search for "GeoCoordinates" in index.html
2. Update latitude/longitude in JSON-LD LocalBusiness schema
3. Update meta geo tags in `<head>` section
4. Verify coordinates match Winchester city center

**Deploy to GitHub Pages:**
1. Commit all changes with descriptive message
2. Push to GitHub: `git push origin main`
3. In GitHub repo settings → Pages, set source to "main" branch, directory "/"
4. Wait 2-3 minutes for deployment
5. Verify site at `https://[username].github.io/[repo-name]/`

## Quality Checklist Before Deployment

- [ ] Zero `[VARIABLE]` placeholders remain
- [ ] Domain correct in all meta tags, canonical, schema, sitemap
- [ ] Geo coordinates accurate for Winchester
- [ ] Email address correct (hello@aiserviceswinchester.co.uk)
- [ ] Cross-links in footer exclude Winchester (current site)
- [ ] Hero subheadline reads uniquely (not templated)
- [ ] FAQ answers use different wording than other satellites
- [ ] GEO/AI statement above footer is unique
- [ ] All Antek Automation and Retell AI links present
- [ ] JSON-LD validates (use Google Rich Results Test)
- [ ] Mobile responsive (test at 320px width)
- [ ] No horizontal scroll on mobile
- [ ] CTAs are solid green (#10b981) with black text

## Winchester-Specific Context

**Coordinates:** 51.0632° N, 1.3080° W
**County:** Hampshire, South East England
**Nearby Towns:** Eastleigh, Romsey, Stockbridge, Alresford, Alton
**Local Landmarks:** Winchester Cathedral, The Great Hall, Wolvesey Castle, Winchester College, city center High Street
**Business Vibe:** Historic cathedral city with blend of professional services (law, finance), independent retailers, tourism/hospitality, and traditional trades serving surrounding villages

Use these details when writing unique, Winchester-specific copy.
