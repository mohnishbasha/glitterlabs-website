# Glitter Technology Ventures Pvt. Ltd. — AI Studio Website

> AI Systems That Deliver Outcomes — Not Just Demos

A complete, production-ready multi-page static website for **Glitter Technology Ventures Pvt. Ltd.**, an AI Studio and Generative AI Content & Distributed AI Teams platform. Built for GitHub Pages deployment — no build step, no server required.

---

## Pages

| File | Route | Description |
|------|-------|-------------|
| `index.html` | `/` | Home — hero, solution pillars, outcomes, content engine, CTA |
| `about.html` | `/about` | Mission, vision, philosophy, audience segments |
| `solutions.html` | `/solutions` | Deep dive: Edge AI, Vertical AI, AI Agents, LLM Frameworks |
| `careers.html` | `/careers` | Open roles: Research Analyst, Growth Manager, AI Engineer |

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Markup | HTML5 (semantic) |
| Styling | [Tailwind CSS](https://tailwindcss.com/) via CDN |
| Fonts | [Inter](https://fonts.google.com/specimen/Inter) via Google Fonts |
| Icons | Inline SVG (Heroicons-style) |
| Hosting | GitHub Pages (static) |
| JavaScript | Vanilla JS — scroll animations, mobile nav, active nav state |

No build tools. No npm. No framework. Deploys directly from the repo root.

---

## Design System

### Colors

| Role | Value |
|------|-------|
| Background | `#030712` (gray-950) |
| Surface | `rgba(255,255,255,0.05)` + `backdrop-filter: blur(16px)` |
| Accent Purple | `#9333ea` → `#c084fc` |
| Accent Blue | `#3b82f6` → `#60a5fa` |
| Accent Neon | `#39FF14` |
| Text Primary | `#ffffff` |
| Text Secondary | `#9ca3af` (gray-400) |

### Key CSS Classes

```css
.glass          /* glassmorphism card surface */
.glass-dark     /* dark navbar / overlay surface */
.gradient-text  /* purple → blue → neon green text gradient */
.gradient-bg    /* animated hero background */
.card-hover     /* lift + glow on hover */
.btn-primary    /* purple-to-blue gradient CTA button */
.btn-ghost      /* outlined ghost button */
.neon-dot       /* pulsing green status indicator */
.grid-bg        /* subtle dot/grid background overlay */
```

### Typography
- Font: **Inter** (300–900 weight range)
- Headings: `font-black` (900), tight tracking
- Body: `text-gray-400`, relaxed line-height
- Code/mono: system monospace stack

### Animation
- Hero background: `gradient-x` keyframe (8s infinite)
- Floating orbs: `float` keyframe (6s ease-in-out)
- Scroll reveal: `IntersectionObserver` fade + slide up
- Hover transitions: `transform: translateY(-4–6px)` + shadow

---

## Project Structure

```
glitterlabs/
├── index.html        # Home page
├── about.html        # About page
├── solutions.html    # Solutions deep dive
├── careers.html      # Open roles
├── Prompt.md         # Original product brief
├── README.md         # This file
├── CLAUDE.md         # Claude Code instructions
└── Skills.md         # Reusable patterns & component guide
```

---

## Deployment

### GitHub Pages + Custom Domain

The repo includes a `CNAME` file pre-configured for `www.glitterlabs.com`.

1. Push this repo to GitHub
2. Go to **Settings → Pages**
3. Set source: **Deploy from branch → `main` → `/ (root)`**
4. Under **Custom domain**, enter `www.glitterlabs.com` and save
5. At your DNS registrar, add these records:

| Type | Name | Value |
|------|------|-------|
| `CNAME` | `www` | `<username>.github.io` |
| `A` | `@` | `185.199.108.153` |
| `A` | `@` | `185.199.109.153` |
| `A` | `@` | `185.199.110.153` |
| `A` | `@` | `185.199.111.153` |

6. Enable **Enforce HTTPS** in Pages settings once DNS propagates (up to 24h)
7. Site will be live at: **https://www.glitterlabs.com**

### Local Preview

Open any `.html` file directly in a browser — or use a local static server:

```bash
# Python
python3 -m http.server 8080

# Node (npx)
npx serve .

# VS Code
# Install "Live Server" extension → right-click index.html → Open with Live Server
```

---

## SEO

Each page includes:
- `<meta charset>` and `<meta viewport>`
- Descriptive `<title>` tags
- `<meta name="description">` with page-specific copy
- `<meta property="og:*">` Open Graph tags for social sharing
- Semantic HTML structure (`<nav>`, `<section>`, `<footer>`, `<h1>`–`<h3>`)

---

## Customization Guide

### Update Contact Email
Search and replace `projects@glitterlabs.com` across all HTML files.

### Update Company Name / Logo
- Logo text: search for `Glitter Technology Ventures Pvt. Ltd.` in all files
- Logo icon letter: search for the `<div>` containing `font-black">G`

### Add a New Role (Careers)
Copy one of the role card `<div>` blocks in `careers.html` and update:
- Role title, description, tags
- `mailto:?subject=Application: <Role Name>`

### Update Social Links
Search for `href="#"` within the `<footer>` sections to replace with real LinkedIn / X URLs.

### Add a New Page
1. Copy any existing page as a template
2. Update the `<title>`, `<meta>`, and `<h1>` tags
3. Add a nav link in all 4 pages' `<nav>` and mobile menu sections

---

## Content Sections Reference

### index.html
- Hero (gradient animated, full-viewport)
- Stats bar (4 headline metrics)
- Solution Pillars (4-card grid, Problem → Solution → Outcome)
- Outcomes / Use Cases (3 metric cards + 4 use case tiles)
- Content & Distributed AI Teams Engine (diagram + feature list)
- CTA section

### about.html
- Hero
- Why We Exist (narrative + 3 framing cards)
- Mission & Vision (2-col cards)
- Philosophy (6-value grid)
- Who We Build For (3 audience segments)
- AI + Workforce Transformation
- CTA

### solutions.html
- Hero + sticky pillar navigation
- Edge AI (architecture diagram, use cases, outcome bars)
- Vertical AI (architecture diagram, use cases, outcome bars)
- AI Agents (multi-agent architecture, human+AI model)
- LLM Frameworks (production LLM stack diagram, components)
- CTA

### careers.html
- Hero (with skill tags)
- Why Join (6 culture cards)
- Open Roles (3 detailed role cards with Apply Now links)
- Open Application CTA

---

## License

© 2026 Glitter Technology Ventures Pvt. Ltd.. All rights reserved.
