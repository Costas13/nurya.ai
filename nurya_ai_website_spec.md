# nurya.ai — Landing Page Specification

## Context

Nurya (nurya.ai) is a computational neuroscience startup building biophysics-based foundational models of the brain for therapeutic target discovery in mental health disorders. The company was previously known as Antikythera Neuro, then briefly neuralis.ai, and has settled on **Nurya** with the domain **nurya.ai**.

This document specifies a minimal "coming soon" landing page to be deployed via **GitHub Pages**, following the same workflow used for the founder's academic lab website at anastassioulab.org (hosted on GitHub Pages with a custom domain).

This is a starting website only. A professional designer will build the full site after the company raises its seed round. The goal here is a clean, premium placeholder that signals credibility to investors who look up the company.

---

## Hosting & Deployment

- **Platform:** GitHub Pages
- **Repository:** Create a new repo (e.g., `nurya-ai/nurya.ai` or similar org/repo structure)
- **Custom domain:** nurya.ai
- **CNAME file:** Include a `CNAME` file in the repo root containing `nurya.ai`
- **SSL:** GitHub Pages provides free SSL — ensure HTTPS is enforced
- **DNS:** After deploying, the user will configure DNS at their domain registrar to point to GitHub Pages (A records to GitHub's IPs + CNAME for www)

---

## Design Direction

### Overall Aesthetic
- **Dark, premium, minimal.** Think high-end biotech meets frontier AI.
- The page should feel like a digital business card — clean, intentional, and confident.
- No navigation menu, no footer clutter, no unnecessary elements.
- The page is a single viewport — no scrolling needed (or minimal scrolling on mobile).

### Color Palette
- **Background:** Very dark — black (#000000) or dark blue-charcoal (#0d1b2a or similar). Should complement the neural imagery.
- **Text:** White or very light gray for maximum contrast.
- **Accent colors (from the logo):** Teal (#00b4d8 range) and magenta/pink (#c77dff or #e040a0 range) — the teal-to-magenta gradient that characterizes the Nurya logo. These can be used subtly (e.g., a thin line, a subtle glow) but sparingly.

---

## Layout Specification

### Structure (top to bottom, vertically centered)

1. **Full-bleed background image** — The cortical column neural visualization (provided as a separate image file). This should cover the entire viewport as a background image with:
   - `background-size: cover`
   - `background-position: center`
   - A dark gradient overlay on top of the image to ensure text readability. Something like a semi-transparent dark overlay (e.g., `rgba(0,0,0,0.5)` to `rgba(0,0,0,0.7)`) — adjust opacity so the neural imagery is visible but text reads cleanly on top.

2. **Centered content block** (vertically and horizontally centered on the page):
   - **Logo mark** — The Nurya spike-N logo (white version), displayed at a reasonable size (roughly 80–120px wide).
   - **Company name** — "nurya" in lowercase, clean sans-serif font (e.g., Inter, or a similar modern geometric sans-serif). White text, light weight. Sized prominently but not overwhelming (~48–64px on desktop).
   - **Tagline** — "BIOPHYSICS-BASED FOUNDATIONAL MODELS OF THE BRAIN" in uppercase, letter-spaced, small size (~12–14px), light gray or white with reduced opacity. This matches the tagline shown on the logo sheet.
   - **Spacer** — Some vertical breathing room (~40–60px).
   - **"Coming Soon"** — Simple, understated. Could be slightly smaller than the company name, perhaps in a lighter weight or reduced opacity.

3. **Contact email** (bottom of page or below the centered block):
   - `info@nurya.ai` (or whatever contact email Costas sets up) — small, subtle, clickable mailto link.

### Responsive Behavior
- On mobile, the layout should scale gracefully. The background image should still cover the viewport. Text sizes should scale down proportionally.
- The cursor-following logo effect (see below) should be disabled on touch devices since there's no cursor.

---

## Cursor Logo Effect

### Description
On desktop, the default cursor should be replaced (or accompanied) by the Nurya logo mark (white version) that follows the mouse pointer. This is the same effect used on anastassioulab.org.

### Implementation Approach
- Use JavaScript to track `mousemove` events.
- Position a small version of the logo (roughly 30–40px) at the cursor position using `position: fixed` and `transform: translate()`.
- Hide the default cursor with `cursor: none` on the body.
- The logo should follow the cursor smoothly (optionally with a slight easing/lag for a polished feel).
- On mobile/touch devices: disable this effect entirely (detect via `matchMedia('(hover: hover)')` or similar). Show the default cursor or no custom cursor.
- The logo used for the cursor should be the **icon-only** version (just the spike-N mark, no wordmark), using the white PNG provided (`nurya_logo_white.png`).

### Reference
See anastassioulab.org for the live implementation of this effect. The lab crest follows the cursor as the user moves the mouse around the page.

---

## Assets Provided

The following files will be provided to Claude Code:

| File | Purpose |
|------|---------|
| `nurya_logo_white.png` | White logo on transparent background — for cursor effect and centered display |
| `nurya_logo_black.png` | Black logo on transparent background — backup/alternative |
| `hero_image.png` (or .jpg) | The cortical column neural visualization — 4th image option selected: panoramic view showing dense dendritic/axonal arbors (teal, blue, gold colored neural processes) with multiple glowing white cell bodies (somata) distributed throughout, resembling a constellation |

**Note:** The hero image comes from the founder's biophysical cortical column simulations — these are real scientific visualizations, not stock illustrations or AI-generated art. This is an important distinction for credibility.

---

## Typography

- **Primary font:** Inter (available from Google Fonts) or a similar clean, modern sans-serif.
- **Company name:** Light or regular weight, ~48–64px desktop.
- **Tagline:** Regular weight, uppercase, letter-spacing ~2–4px, ~12–14px.
- **"Coming Soon":** Light weight, ~20–24px.
- **Contact email:** Regular weight, ~12–14px.

---

## Technical Notes

- **Single file:** Everything should be in a single `index.html` file (inline CSS and JS). Keep it simple — no build tools, no frameworks, no npm.
- **Google Fonts:** Load Inter (or chosen font) from Google Fonts CDN.
- **Performance:** Optimize the hero image (compress to reasonable file size). Consider using a high-quality JPEG rather than PNG for the background to keep load times fast.
- **Favicon:** Use the Nurya logo mark as the favicon. Generate a simple favicon from the provided logo.
- **Meta tags:** Include basic meta tags for SEO and social sharing:
  - `<title>Nurya — Biophysics-Based Foundational Models of the Brain</title>`
  - `<meta name="description" content="Nurya builds biophysics-based foundational models of the brain for therapeutic target discovery in mental health disorders.">`
  - Open Graph tags for social sharing (og:title, og:description, og:image using the hero image or logo)
- **No analytics:** Not needed at this stage.
- **No cookie banners:** Not needed — no tracking.

---

## File Structure in Repo

```
nurya.ai/
├── index.html          # Single-page site (HTML + inline CSS + inline JS)
├── CNAME               # Contains: nurya.ai
├── images/
│   ├── hero.jpg        # Cortical column background image
│   ├── logo_white.png  # White logo for cursor + display
│   └── favicon.ico     # Favicon generated from logo
└── README.md           # Brief repo description
```

---

## What NOT to Include

- No navigation bar
- No hamburger menu
- No footer with links
- No social media icons
- No blog section
- No team page
- No animations beyond the cursor effect (keep it fast and clean)
- No JavaScript frameworks
- No cookie consent banners
- No analytics scripts

---

## Summary Checklist

- [ ] Create GitHub repo with GitHub Pages enabled
- [ ] Single `index.html` with dark theme, full-bleed neural background image
- [ ] Dark overlay on background for text readability
- [ ] Centered: logo mark → "nurya" → tagline → "Coming Soon"
- [ ] Cursor-following logo effect (desktop only)
- [ ] CNAME file for nurya.ai
- [ ] Favicon from logo
- [ ] Meta tags for SEO and social sharing
- [ ] Responsive design (works on mobile)
- [ ] Contact email at bottom
- [ ] DNS configuration instructions provided
