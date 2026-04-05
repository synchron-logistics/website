# Roadmap

Build status for the Synchron Logistics website.

---

## Already Built

### Infrastructure
- [x] Astro 4 project scaffold
- [x] Tailwind CSS integration with custom design tokens (brand-red, brand-dark, brand-light)
- [x] Google Fonts loaded (Barlow Condensed, Barlow)
- [x] `Layout.astro` base shell with global styles and scripts
- [x] `site.config.js` — central client config (business details + module toggles + email routing)
- [x] `tailwind.config.mjs` — design token definitions

### Components
- [x] `Nav.astro` — top bar (conditional phone), sticky nav, desktop links, mobile hamburger. Pulls from site.config.js. Null-safe for missing phone.
- [x] `Footer.astro` — 4-column layout. Credentials line (IATA/FMC). Null-safe for missing phone/address.

### Pages
- [x] `index.astro` — Hero (global reach + reliability), Asia Pacific differentiator strip, Origin/Mission section, Services (3 cards), Stats bar (2015 / 1,000+ / 10 / 24/7), CTA
- [x] `about.astro` — Page header (IATA/FMC in intro), Origin story, Vision + Mission, Compliance section, Accreditations section
- [x] `services.astro` — Page header, 4 service groups (Domestic / International / Warehousing / Value-Added), Industries We Serve grid (10 industries), CTA
- [x] `contact.astro` — Contact info (null-safe), Quote form with inquiry type dropdown (email routing comments in place)
- [x] `tracking.astro` — Honest placeholder: portal context, portal features preview, Contact CTA
- [x] `carriers.astro` — NEW: Hero, Why Partner, Owner-Operators, Payment Terms, What We Look For, Apply CTA

### Animations
- [x] Hero page-load stagger (fade-slide-up, CSS keyframes, 5-element stagger)
- [x] Hero infinite float
- [x] Scroll reveal (`.reveal` class, IntersectionObserver, respects `prefers-reduced-motion`)
- [x] Counter animation (stats section, eased, respects `prefers-reduced-motion`)
- [x] Nav scroll shadow
- [x] Service card hover: lift + shadow + image zoom + overlay
- [x] Industries grid: icon + label colour transition on hover
- [x] Read more arrow shift on hover

### Content
- [x] Founded year corrected: 2015 (was incorrectly 2000)
- [x] Stats updated: 2015 / 1,000+ carriers / 10 industries / 24/7/365
- [x] Email routing added to site.config.js: general / sales / accounting
- [x] IATA and FMC/NVOCC credentials: in About page copy, in About accreditations section, in footer bottom bar
- [x] Asia Pacific differentiator: homepage strip (2nd busiest airport / 3rd busiest port)
- [x] Mission verbatim: "Driven by purpose. Fueled by opportunity."
- [x] Vision verbatim: "To find challenging logistics solutions and make the improbable possible."
- [x] Compliance section: fraud prevention, human rights, conflicts of interest, antitrust
- [x] Services restructured into 4 groups with 11 individual services
- [x] Industries grid: 10 sectors with inline SVG icons
- [x] Carriers page: full carrier partnership content with payment terms

---

## In Progress

- [ ] **Placeholder contact details** — phone and street address still MISSING. Marked with TODO in site.config.js. City/province (Kelowna, BC) confirmed; full street address and postal not yet provided.
- [ ] **Social media URLs** — all `#` placeholders in site.config.js. Client has not provided.
- [ ] **Carrier application link** — `/carriers` CTA button points to `#`. Needs client-provided URL or form spec.
- [ ] **Tracking portal URL** — Synch101 app status and portal URL not yet confirmed by client.
- [ ] **Resend contact form** — form UI complete with inquiry type dropdown; API endpoint not yet built.

---

## Still Needed

### Content confirmation required
- [ ] Real phone number — update `site.phone` and `site.phoneHref` in site.config.js
- [ ] Real street address + postal code — update `site.address` in site.config.js
- [ ] Social media URLs — update `site.social` in site.config.js
- [ ] Carrier application form/link — update `/carriers` CTA
- [ ] Tracking portal URL — update `tracking.astro` with real login link or embed
- [ ] Hero images — confirm licensing of Unsplash images used in dev, or replace with client-provided assets

### Features to build
- [ ] Resend contact form backend (`src/pages/api/contact.ts`)
  - Read `inquiryType` from form, map to correct email from site.config.js `emails`
  - Server-side validation
  - Success/error state handling in form UI
- [ ] Privacy Policy page (`/privacy`)
- [ ] Terms of Service page (`/terms`)
- [ ] 404 page
- [ ] Favicon + social share image (OG image)
- [ ] Sitemap (`@astrojs/sitemap` integration)

### Launch checklist
- [ ] Replace all Unsplash images with licensed or client-provided assets
- [ ] Confirm and fill all `// TODO: MISSING` fields in site.config.js
- [ ] Wire contact form to Resend
- [ ] Set up Cloudflare Pages deployment
- [ ] Set Resend API key in Cloudflare Pages environment variables
- [ ] Test on mobile (iOS Safari, Android Chrome)
- [ ] Lighthouse audit (performance, accessibility, SEO)
- [ ] Cross-browser check (Chrome, Safari, Firefox, Edge)
