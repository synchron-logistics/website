# CLAUDE.md — Project Briefing

This file is the primary briefing document for AI assistants working on this project.
Read this before making any changes.

---

## Dual Purpose

This project serves two simultaneous goals:

1. **Client Delivery** — Build and ship the Synchron Logistics website
2. **Template Foundation** — Establish the master `astro-template` pattern for Omnia Marketing's future client projects

When making architectural decisions, consider both purposes. Patterns introduced here will be replicated across future client sites. Prefer clarity and reusability over one-off shortcuts.

---

## Client

- **Business:** Synchron Logistics
- **Location:** Kelowna, BC, Canada
- **Industry:** Logistics / Transportation
- **CMS:** None — fully static site

All client-specific details live in `site.config.js`. **Do not hardcode business details in components.**

---

## Stack

| Layer | Technology |
|---|---|
| Framework | Astro 4 |
| Styling | Tailwind CSS 3 |
| Deployment | Cloudflare Pages |
| Email (forms) | Resend |
| CMS | None |
| Database | None |

---

## Active Modules

Controlled via `modules` export in `site.config.js`:

| Module | Status | Notes |
|---|---|---|
| `contactForm` | Active | UI built; Resend backend not yet wired |
| `carriers` | Active | `/carriers` page built; apply link pending from client |
| `tracking` | Active | UI placeholder — portal URL pending from client |
| `industries` | Active | Industries grid on `/services` page |
| `blog` | Off | Not needed for this client |
| `gallery` | Off | Not needed for this client |
| `testimonials` | Off | Not needed for this client |
| `cms` | Off | Static site only |

---

## Pages

| Route | File | Status |
|---|---|---|
| `/` | `src/pages/index.astro` | Built — hero, Asia Pacific strip, origin/mission, services, stats, red CTA |
| `/about` | `src/pages/about.astro` | Built — origin story, vision, mission, compliance, IATA/FMC accreditations |
| `/services` | `src/pages/services.astro` | Built — alternating split layout, 4 groups, real images, industries grid |
| `/contact` | `src/pages/contact.astro` | Built — form UI with inquiry type routing; Resend backend pending |
| `/tracking` | `src/pages/tracking.astro` | Built — honest placeholder; portal URL pending from client |
| `/carriers` | `src/pages/carriers.astro` | Built — full carrier partnership page; apply link pending from client |

---

## Current Build Status

- Design system established (tokens, fonts, component patterns)
- All 6 pages built with real content and layout
- `.gitignore` in place — node_modules and build artifacts excluded
- Animations: scroll reveal, hero stagger, counter (1000 and 10 only), hover states
- Nav and Footer built, responsive, null-safe for missing phone/address
- All business details in `site.config.js` — no hardcoded strings in components
- Services page: full alternating split layout with 4 real client images
- Contact form: UI complete with inquiry type dropdown; Resend backend not yet built
- Missing from client: phone, street address, postal code, social URLs, carrier apply link, tracking portal URL

---

## Rules for This Project

1. **Always read `site.config.js` and `CONVENTIONS.md` before writing any new component or page.**

2. **No hardcoded business details.** All contact info, names, taglines, and copy that varies per client must live in `site.config.js`.

3. **Follow the design conventions in `CONVENTIONS.md` exactly.** No new colors without adding them to `tailwind.config.mjs`. No border-radius on buttons or inputs (sharp aesthetic).

4. **Mobile-first.** Write base styles for mobile, then layer `md:` and `lg:` breakpoints.

5. **Respect `prefers-reduced-motion`.** Wrap all non-trivial CSS animations in `@media (prefers-reduced-motion: no-preference)`.

6. **No new features before existing placeholders are resolved.** The contact form must be wired to Resend before adding new form fields. The tracking page must be scoped before adding tracking logic.

7. **Keep `Layout.astro` lean.** Global scripts and styles only — no page-specific logic in the layout.

8. **Do not create new files unnecessarily.** Prefer editing existing components to adding new ones.

9. **Confirm real client details before launch.** Phone, street address, postal code, and social links in `site.config.js` are still `null` / `#` placeholders — all marked with `// TODO: MISSING`. Stats (2015, 1,000+, 10 industries, 24/7/365) are confirmed real values. Flag any remaining placeholder data before merging to production.

10. **This is a template foundation.** Any pattern established here should be documented in `CONVENTIONS.md`. If a pattern is one-off and not reusable, note that explicitly.

---

## Key Files

| File | Purpose |
|---|---|
| `site.config.js` | Client config — business details and module toggles |
| `tailwind.config.mjs` | Design tokens — colors and fonts |
| `src/layouts/Layout.astro` | Base HTML shell, global styles, global scripts |
| `src/components/Nav.astro` | Site navigation |
| `src/components/Footer.astro` | Site footer |
| `CONVENTIONS.md` | Design system and coding conventions |
| `ROADMAP.md` | What's built, in progress, and still needed |
| `AGENCY.md` | Omnia agency dashboard integration (pending) |

---

## Resend Integration (Pending)

The contact form at `/contact` needs to be wired to Resend for email delivery.

**Approach when ready:**
- Add `resend` npm package
- Create an Astro API endpoint at `src/pages/api/contact.ts`
- The endpoint receives form POST, validates fields, sends via Resend
- Add Resend API key to Cloudflare Pages environment variables
- Handle success/error states in the form UI
