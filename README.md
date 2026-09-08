
# Omnibus Solutions — Website

A static, multi-page marketing site for Omnibus Solutions, a company that offers two things under one roof: **custom software / digital services** and **HR consultancy / job-ready talent acquisition**. The design treats that duality as the core idea rather than hiding it — see "Design concept" below.

No build tools, frameworks, or dependencies. Plain HTML, CSS, and vanilla JS. Open any page directly in a browser or serve the folder with any static host.

---

## File structure

```
omnibus/
├── index.html          Home — dual hero, service overviews, stats, testimonials
├── it-services.html    IT & Digital Services (software, mobile, SEO)
├── hr-talent.html      HR & Talent Solutions (staffing, recruitment)
├── about.html          About Us
├── contact.html        Contact — dual-routed lead form
├── css/
│   └── style.css       Full design system (tokens, layout, components)
├── js/
│   └── main.js         Nav toggle, scroll reveal, stat counters, tabs, form logic
└── README.md
```

Every page shares the same `<nav>` and `<footer>` markup and pulls from the same `css/style.css` and `js/main.js` — edit either file once and the change applies site-wide.

---

## Design concept

**The idea:** Omnibus is two practices — Technology and Talent — that don't want to feel like two different companies bolted together. The site expresses that with a consistent "seam" motif: a two-color gradient line (signal blue → emerald) that appears in the hero, section dividers, and footer, literally stitching the two halves of the business into one visual system.

| Register | Color | Display typeface | Where it shows up |
|---|---|---|---|
| Technology | Navy `#0E1B2C` + Signal blue `#4E86F5` | Space Grotesk | IT sections, dark backgrounds |
| Human / Talent | Warm paper `#F4F3EC` + Emerald `#1F8A63` | Newsreader (italic) | HR sections, light backgrounds |
| Shared | — | IBM Plex Sans (body) / IBM Plex Mono (labels, data, nav) | Everywhere |

The homepage hero is a literal split screen — navy/Tech on one side, paper/Human on the other — so a first-time visitor understands the dual offering in under three seconds, per the original brief.

---

## Pages at a glance

- **Home** — dual hero with two CTAs, IT services overview, HR services overview, "Omnibus Advantage" quote block, animated stats, tech-stack marquee, tabbed testimonials (Software Clients / Recruitment Partners).
- **IT & Digital Services** — service breakdown (software, mobile, SEO), 4-step build process, tech stack marquee, cross-sell CTA into talent.
- **HR & Talent Solutions** — value pillars (pre-vetted, zero onboarding lag, flexible models), 4-step placement process, roles placed most often, cross-sell CTA into IT.
- **About Us** — origin story, how the two practices are structured, shared standards.
- **Contact** — dual-path form: visitor picks "I want to build a product" or "I need to hire talent" and the form routes/labels the inquiry accordingly (client-side only — see "Wiring the form" below).

---

## Wiring the form

`contact.html` currently only simulates a submission (shows a success message, does not send data anywhere). To make it functional, wire the `.contact-form` submit handler in `js/main.js` to one of:

- A form backend (Formspree, Getform, Basin) — swap the `preventDefault` block for a `fetch()` POST.
- A serverless function that emails the right inbox based on `inquiry-path` (`tech` or `human`).
- A CRM webhook (HubSpot, Pipedrive) if lead routing needs to land directly in a pipeline.

---

## Customizing

- **Copy:** all page copy lives directly in the HTML — no CMS or templating layer.
- **Colors/fonts:** every token is a CSS custom property at the top of `css/style.css` under `:root`. Change a value there and it cascades everywhere.
- **Stats counters:** edit the `data-count` / `data-suffix` attributes on `.stat-num` elements in `index.html`.
- **New pages:** copy the `<nav>` and `<footer>` block from any existing page to keep navigation consistent, and mark the current page's link with `class="active"`.

---

## Browser support & accessibility

- Responsive down to ~360px; hero and grids collapse to single-column on mobile.
- Keyboard focus is visible (`:focus-visible` outline) on all interactive elements.
- Marquee and scroll-reveal animations respect `prefers-reduced-motion`.
- Semantic landmarks (`nav`, `header`, `section`, `footer`) throughout.

## Not yet included

- Backend/CMS integration (copy is static HTML)
- JobPosting / Organization / Service schema markup (recommended in the original brief — straightforward to add as JSON-LD in each page's `<head>`)
- Real photography/team imagery — current build is copy- and layout-first
