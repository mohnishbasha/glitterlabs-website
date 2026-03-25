# CLAUDE.md — Glitter Technology Ventures Pvt. Ltd. Website

Instructions for Claude Code when working on this project.

---

## Project Overview

Static multi-page website for Glitter Technology Ventures Pvt. Ltd. — an AI Studio and Generative AI Content & Distributed AI Teams platform. Four HTML pages, no build tools, deployed via GitHub Pages.

**Key constraint:** This is a pure static site. No npm, no bundler, no server-side code. All changes must remain deployable by opening an HTML file directly in a browser or pushing to GitHub Pages.

---

## File Map

```
index.html      Home page (hero, pillars, outcomes, content engine)
about.html      About (mission, vision, philosophy, audience)
solutions.html  Solutions deep dive (4 pillars with architecture diagrams)
careers.html    Careers (3 open roles + open application)
Prompt.md       Original product brief — do not modify unless explicitly asked
README.md       Project documentation
CLAUDE.md       This file
Skills.md       Reusable component patterns and design system reference
```

---

## Rules

### Always
- Maintain the shared design system (colors, glassmorphism, gradient-text) across all pages
- Keep all inter-page navigation links consistent — if a nav link changes in one file, update it in all four
- Use inline SVG for icons — no external icon library CDN calls
- Use `mailto:projects@glitterlabs.com` for all contact and apply links
- Preserve SEO meta tags (`<title>`, `<meta name="description">`, `<meta property="og:*">`) when editing pages

### Never
- Add npm, a bundler, or any server-side dependency
- Add a fifth external CDN beyond Tailwind CSS and Google Fonts
- Remove the `scroll-smooth` class from `<html>` — smooth scrolling is intentional
- Break the `IntersectionObserver` scroll-reveal pattern — it's on every page
- Use `!important` in inline styles or `<style>` blocks unless absolutely necessary
- Commit changes to `Prompt.md` unless the user explicitly asks to update the brief

---

## Design System

### Color Tokens

| Token | Value | Usage |
|-------|-------|-------|
| Background | `bg-gray-950` | Page background |
| Glass surface | `rgba(255,255,255,0.05)` + `backdrop-filter:blur(16px)` | Cards, modals |
| Dark glass | `rgba(0,0,0,0.3)` + `backdrop-filter:blur(16px)` | Navbar |
| Purple accent | `#9333ea` → `#c084fc` | Primary CTAs, highlights |
| Blue accent | `#3b82f6` → `#60a5fa` | Secondary accents |
| Neon green | `#39FF14` | Status dots, live indicators |
| Body text | `text-gray-400` | Paragraph text |
| Heading text | `text-white font-black` | All major headings |

### Core CSS Classes (defined in `<style>` on each page)

```css
.glass          /* Card surface: rgba(255,255,255,0.05) + blur */
.glass-dark     /* Navbar: rgba(0,0,0,0.3) + blur */
.gradient-text  /* Purple-blue-neon gradient on text */
.gradient-bg    /* Animated hero background */
.card-hover     /* Lift on hover: translateY(-4 to -6px) */
.btn-primary    /* Purple → blue gradient button */
.btn-ghost      /* Outlined ghost button */
.neon-dot       /* 8px green pulsing dot */
.grid-bg        /* Subtle grid pattern overlay */
```

These classes are redefined in each page's `<style>` block. If you modify one, update all four pages to stay consistent.

### Typography Rules
- All headings: `font-black` (weight 900)
- Page titles / hero: `text-5xl md:text-6xl` or `text-5xl md:text-7xl`
- Section headings: `text-4xl md:text-5xl font-black`
- Card headings: `text-xl font-bold` or `text-2xl font-bold`
- Body copy: `text-gray-400 leading-relaxed`
- Labels / badges: `text-xs font-semibold uppercase tracking-widest`

---

## Navigation Structure

Every page shares the same navbar and footer. When updating links, update all four files.

**Navbar links:**
```
Home → index.html
Solutions → solutions.html
About → about.html
Careers → careers.html
Contact → mailto:projects@glitterlabs.com
CTA button → mailto:projects@glitterlabs.com (text: "Partner With Us")
```

**Footer quick links:** Same as above (Home, Solutions, About, Careers).

**Mobile menu:** Toggled by `onclick="document.getElementById('mobile-menu').classList.toggle('hidden')"` — no JS function needed, pure class toggle.

---

## Page-Specific Notes

### index.html
- The hero uses three layered animated orbs (`animate-pulse-slow`, `animate-float`) — keep these for visual depth
- The "Distribution Engine" panel uses fake live terminal output — this is intentional, decorative
- The stats bar (70%, 10x, <50ms, ∞) sits between the hero and solutions — do not remove it
- Solution cards use the `Problem → Solution → Outcome` format — maintain this structure

### solutions.html
- Has a `pillar-nav` sticky scroll navigation — links use `#edge`, `#vertical`, `#agents`, `#llm` fragment IDs
- The `IntersectionObserver` scroll listener at the bottom updates the active pillar nav link
- Architecture diagrams use `.arch-box` and `.arch-arrow` classes — keep these for visual consistency
- Progress bars use inline `width` style (e.g., `style="width:95%"`) — these are intentional data representations

### careers.html
- Role `mailto:` links include a subject line: `?subject=Application: <Role Name>` — preserve this
- The "Don't See Your Role?" section is important for inbound — keep it at the bottom of the roles
- Role cards use a 3-color system: purple (Research), blue (Growth), green (AI Engineer)

### about.html
- The "Why We Exist" section uses `border-left` colored lines (`.value-line` class) — intentional design detail
- The philosophy grid is 3×2 — maintain the 6 values if adding/removing

---

## Editing Patterns

### Adding a new section to a page
1. Copy the nearest structurally similar section
2. Update the badge label, heading, and copy
3. Ensure the wrapping `<section>` has `py-24 px-6` padding and a `scroll-mt-20` if it has an anchor ID
4. Inner content wrapper: `max-w-6xl mx-auto` or `max-w-7xl mx-auto`

### Adding a new open role to careers.html
Copy an existing role card `<div class="glass card-hover rounded-2xl p-8 border border-white/5">` block and update:
- Icon emoji and gradient colors
- Title, tags, description
- "You'll work on" bullet points
- `mailto:?subject=Application: <Title>` link

### Changing the hero headline
Edit the `<h1>` in the relevant page — the `gradient-text` span wraps the colored portion. Keep the two-line structure for visual rhythm.

### Updating outcome metrics
Search for the specific number (e.g., `70%`) across all pages. The same metrics appear in:
- `index.html` — stats bar and outcomes section
- `solutions.html` — outcome progress bars

---

## Scroll Reveal Animation

All pages use this pattern at the bottom of `<body>`:

```js
const observer = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.style.opacity = '1';
      e.target.style.transform = 'translateY(0)';
    }
  });
}, { threshold: 0.1 });

document.querySelectorAll('section > div').forEach(el => {
  el.style.opacity = '0';
  el.style.transform = 'translateY(20px)';
  el.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
  observer.observe(el);
});
```

This targets `section > div` — keep the `<section>` → `<div class="max-w-*">` structure intact or animations will not fire.

---

## Tailwind Configuration

Each page includes an inline Tailwind config extending the default theme:

```js
tailwind.config = {
  theme: {
    extend: {
      animation: {
        'gradient-x': 'gradient-x 8s ease infinite',
        'float': 'float 6s ease-in-out infinite',
        'pulse-slow': 'pulse 4s cubic-bezier(0.4,0,0.6,1) infinite',
      },
      keyframes: {
        'gradient-x': { ... },
        'float': { ... },
      },
    },
  },
}
```

Do not remove these — `animate-gradient-x`, `animate-float`, and `animate-pulse-slow` classes depend on them.

---

## Domain & Canonical URLs

The site is hosted at `https://www.glitterlabs.com`. Each page has:
- `<link rel="canonical" href="https://www.glitterlabs.com/<page>.html" />` in `<head>`
- `<meta property="og:url" content="https://www.glitterlabs.com/<page>.html" />` in `<head>`
- A `CNAME` file in the repo root containing `www.glitterlabs.com` (required by GitHub Pages for custom domains)

If the domain ever changes, update the canonical and og:url tags in all 4 HTML files and replace the `CNAME` file content.

---

## Do Not Change Without Discussion

- The company name "Glitter Technology Ventures Pvt. Ltd." — update site-wide if the user requests a rename
- The 4-pillar solution structure (Edge AI, Vertical AI, AI Agents, LLM Frameworks)
- The 3 open roles (Software Research Analyst, Growth & Partnerships Manager, AI Engineer)
- The contact email `projects@glitterlabs.com`
- `Prompt.md` content — this is the source-of-truth brief, only update when explicitly instructed
