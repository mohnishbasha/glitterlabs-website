# Skills.md — Glitter Technology Ventures Pvt. Ltd. Reusable Patterns & Component Guide

A reference library of copy-paste-ready components, patterns, and design primitives used throughout the Glitter Technology Ventures Pvt. Ltd. website.

---

## Table of Contents

1. [Navbar](#navbar)
2. [Hero Section](#hero-section)
3. [Badge / Label](#badge--label)
4. [Glass Card](#glass-card)
5. [Problem → Solution → Outcome Card](#problem--solution--outcome-card)
6. [Architecture Diagram](#architecture-diagram)
7. [Outcome Progress Bar](#outcome-progress-bar)
8. [CTA Section](#cta-section)
9. [Role Card (Careers)](#role-card-careers)
10. [Footer](#footer)
11. [Scroll Reveal Animation](#scroll-reveal-animation)
12. [Animated Background Orbs](#animated-background-orbs)
13. [Gradient Text](#gradient-text)
14. [Neon Status Dot](#neon-status-dot)
15. [Terminal / Live Panel](#terminal--live-panel)
16. [Stats Bar](#stats-bar)
17. [Icon Button](#icon-button)

---

## Navbar

Fixed top navbar with glassmorphism, responsive mobile toggle.

```html
<nav class="fixed top-0 left-0 right-0 z-50 glass-dark">
  <div class="max-w-7xl mx-auto px-6 py-4 flex items-center justify-between">
    <!-- Logo -->
    <a href="index.html" class="flex items-center gap-2">
      <div class="w-8 h-8 rounded-lg bg-gradient-to-br from-purple-500 to-blue-500 flex items-center justify-center text-sm font-black">G</div>
      <span class="text-xl font-black tracking-tight">Glitter Technology Ventures Pvt. Ltd.</span>
    </a>
    <!-- Desktop links -->
    <div class="hidden md:flex items-center gap-8 text-sm font-medium text-gray-300">
      <a href="index.html" class="text-white">Home</a>
      <a href="solutions.html" class="hover:text-purple-400 transition-colors">Solutions</a>
      <a href="about.html" class="hover:text-purple-400 transition-colors">About</a>
      <a href="careers.html" class="hover:text-purple-400 transition-colors">Careers</a>
      <a href="mailto:hello@glitterlabs.com" class="hover:text-purple-400 transition-colors">Contact</a>
    </div>
    <!-- CTA -->
    <a href="mailto:hello@glitterlabs.com" class="hidden md:inline-flex btn-primary text-white text-sm font-semibold px-5 py-2 rounded-full">
      Partner With Us
    </a>
    <!-- Mobile toggle -->
    <button class="md:hidden p-2 rounded-lg glass" onclick="document.getElementById('mobile-menu').classList.toggle('hidden')">
      <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
      </svg>
    </button>
  </div>
  <!-- Mobile menu -->
  <div id="mobile-menu" class="hidden md:hidden glass-dark border-t border-white/5 px-6 py-4 space-y-3 text-sm font-medium text-gray-300">
    <a href="index.html" class="block text-white">Home</a>
    <a href="solutions.html" class="block hover:text-purple-400">Solutions</a>
    <a href="about.html" class="block hover:text-purple-400">About</a>
    <a href="careers.html" class="block hover:text-purple-400">Careers</a>
    <a href="mailto:hello@glitterlabs.com" class="block hover:text-purple-400">Contact</a>
  </div>
</nav>
```

**Active page:** Set the current page's link to `class="text-white"` (remove `hover:text-purple-400`).

---

## Hero Section

Full-viewport animated gradient hero with orbs, badge, headline, and dual CTAs.

```html
<section class="relative min-h-screen flex items-center justify-center overflow-hidden gradient-bg grid-bg">
  <!-- Background orbs -->
  <div class="absolute top-1/4 left-1/4 w-96 h-96 bg-purple-600/20 rounded-full blur-3xl animate-pulse-slow"></div>
  <div class="absolute bottom-1/4 right-1/4 w-80 h-80 bg-blue-600/20 rounded-full blur-3xl animate-pulse-slow" style="animation-delay:2s"></div>

  <div class="relative z-10 max-w-5xl mx-auto px-6 text-center pt-24 pb-16">
    <!-- Badge -->
    <div class="inline-flex items-center gap-2 glass rounded-full px-4 py-2 text-xs font-semibold text-purple-300 mb-8 border border-purple-500/20">
      <div class="neon-dot animate-pulse"></div>
      Tag line here
    </div>
    <!-- Headline -->
    <h1 class="text-5xl md:text-7xl font-black leading-tight mb-6 tracking-tight">
      Main Headline<br/>
      <span class="gradient-text">Colored Part</span>
    </h1>
    <!-- Subheadline -->
    <p class="text-gray-400 text-lg md:text-xl max-w-2xl mx-auto mb-10 leading-relaxed">
      Subheadline copy goes here.
    </p>
    <!-- CTAs -->
    <div class="flex flex-col sm:flex-row gap-4 justify-center">
      <a href="#" class="btn-primary text-white font-semibold px-8 py-4 rounded-full text-sm inline-flex items-center gap-2">
        Primary CTA
        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"/>
        </svg>
      </a>
      <a href="#" class="btn-ghost text-white font-semibold px-8 py-4 rounded-full text-sm inline-flex items-center gap-2">
        Secondary CTA
      </a>
    </div>
  </div>
</section>
```

**Variants:**
- For inner pages (not full-viewport): use `pt-32 pb-20` on section, remove `min-h-screen`
- For smaller heroes: use `text-5xl md:text-6xl` for the `<h1>`

---

## Badge / Label

Small pill label used above section headings.

```html
<!-- Purple variant -->
<div class="inline-flex items-center gap-2 glass rounded-full px-4 py-2 text-xs font-semibold text-purple-300 mb-6 border border-purple-500/20">
  Label Text
</div>

<!-- With live dot -->
<div class="inline-flex items-center gap-2 glass rounded-full px-4 py-2 text-xs font-semibold text-purple-300 mb-6 border border-purple-500/20">
  <div class="neon-dot animate-pulse"></div>
  Live Label
</div>

<!-- Blue variant -->
<div class="inline-flex items-center gap-2 glass rounded-full px-4 py-2 text-xs font-semibold text-blue-300 mb-4 border border-blue-500/20">
  Blue Label
</div>

<!-- Green variant -->
<div class="inline-flex items-center gap-2 glass rounded-full px-4 py-2 text-xs font-semibold text-green-300 mb-4 border border-green-500/20">
  Green Label
</div>
```

---

## Glass Card

Standard glassmorphism card with hover lift.

```html
<div class="glass card-hover rounded-2xl p-8">
  <!-- Icon -->
  <div class="w-14 h-14 rounded-xl bg-gradient-to-br from-purple-600/30 to-purple-900/30 border border-purple-500/20 flex items-center justify-center text-2xl mb-6">
    ⚡
  </div>
  <h3 class="text-2xl font-bold mb-2">Card Title</h3>
  <div class="text-xs font-semibold text-purple-400 uppercase tracking-widest mb-4">Subtitle / Tags</div>
  <p class="text-gray-400 text-sm leading-relaxed">
    Card body content goes here.
  </p>
</div>
```

**Icon color variants:**

| Theme | Gradient | Border |
|-------|----------|--------|
| Purple | `from-purple-600/30 to-purple-900/30` | `border-purple-500/20` |
| Blue | `from-blue-600/30 to-blue-900/30` | `border-blue-500/20` |
| Green | `from-green-600/30 to-emerald-900/30` | `border-green-500/20` |
| Orange | `from-orange-600/30 to-red-900/30` | `border-orange-500/20` |

---

## Problem → Solution → Outcome Card

Used on the Home and Solutions pages.

```html
<div class="glass card-hover rounded-2xl p-8">
  <div class="pillar-icon bg-gradient-to-br from-purple-600/30 to-purple-900/30 border border-purple-500/20 mb-6">⚡</div>
  <h3 class="text-2xl font-bold mb-2">Pillar Name</h3>
  <div class="text-xs font-semibold text-purple-400 uppercase tracking-widest mb-4">Tag · Tag · Tag</div>
  <div class="space-y-3 text-sm text-gray-400">
    <div class="flex gap-3">
      <span class="text-red-400 font-bold shrink-0">Problem →</span>
      <span>The problem statement.</span>
    </div>
    <div class="flex gap-3">
      <span class="text-blue-400 font-bold shrink-0">Solution →</span>
      <span>How we solve it.</span>
    </div>
    <div class="flex gap-3">
      <span class="text-green-400 font-bold shrink-0">Outcome →</span>
      <span>Measurable result.</span>
    </div>
  </div>
  <a href="#" class="mt-6 inline-flex items-center gap-1 text-purple-400 text-sm font-semibold hover:gap-2 transition-all">
    Learn more
    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"/>
    </svg>
  </a>
</div>
```

**Requires this CSS:**
```css
.pillar-icon {
  width: 56px; height: 56px; border-radius: 16px;
  display: flex; align-items: center; justify-content: center;
  font-size: 24px;
}
```

---

## Architecture Diagram

Code-style diagram used on the Solutions page.

```html
<div class="glass rounded-2xl p-7">
  <div class="text-xs font-semibold text-gray-500 uppercase tracking-widest mb-5">Architecture Overview</div>
  <div class="space-y-3">
    <div class="arch-box">📦 Input Layer / Source</div>
    <div class="arch-arrow">↓ Processing Step</div>
    <div class="arch-box">🔧 Core Processing Layer</div>
    <div class="arch-arrow">↓ Distribution Step</div>
    <!-- Multi-column row -->
    <div class="grid grid-cols-3 gap-2">
      <div class="arch-box text-center">Option A</div>
      <div class="arch-box text-center">Option B</div>
      <div class="arch-box text-center">Option C</div>
    </div>
    <div class="arch-arrow">↓ Output</div>
    <!-- Outcome row - use color to indicate result -->
    <div class="arch-box text-green-400">✅ Result description</div>
  </div>
</div>
```

**Requires this CSS:**
```css
.arch-box {
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.08);
  border-radius: 10px; padding: 10px 16px;
  font-size: 12px; font-family: monospace; color: #94a3b8;
}
.arch-arrow {
  color: rgba(255,255,255,0.2); font-size: 18px;
  display: flex; align-items: center; justify-content: center;
}
```

---

## Outcome Progress Bar

Visual representation of measurable outcomes.

```html
<div class="glass rounded-2xl p-7">
  <div class="text-xs font-semibold text-gray-500 uppercase tracking-widest mb-4">Measured Outcomes</div>
  <div class="space-y-4">
    <div>
      <div class="flex justify-between text-sm mb-1">
        <span>Metric Label</span>
        <span class="text-purple-400 font-bold">95%</span>
      </div>
      <div class="h-1 rounded-full bg-gray-800">
        <div class="h-1 rounded-full bg-gradient-to-r from-purple-600 to-purple-400" style="width:95%"></div>
      </div>
    </div>
    <!-- Repeat for each metric -->
  </div>
</div>
```

**Color variants for the fill bar:**

| Theme | Classes |
|-------|---------|
| Purple | `bg-gradient-to-r from-purple-600 to-purple-400` |
| Blue | `bg-gradient-to-r from-blue-600 to-blue-400` |
| Green | `bg-gradient-to-r from-green-600 to-green-400` |
| Orange | `bg-gradient-to-r from-orange-600 to-orange-400` |

---

## CTA Section

Full-width centered CTA with gradient overlay and glow.

```html
<section class="py-24 px-6">
  <div class="max-w-4xl mx-auto text-center">
    <div class="glass rounded-3xl p-12 md:p-16 relative overflow-hidden">
      <!-- Gradient overlay -->
      <div class="absolute inset-0 bg-gradient-to-br from-purple-900/40 via-transparent to-blue-900/40 pointer-events-none"></div>
      <!-- Orb accents -->
      <div class="absolute top-0 left-0 w-64 h-64 bg-purple-600/10 rounded-full blur-3xl -translate-x-1/2 -translate-y-1/2"></div>
      <div class="absolute bottom-0 right-0 w-64 h-64 bg-blue-600/10 rounded-full blur-3xl translate-x-1/2 translate-y-1/2"></div>

      <div class="relative z-10">
        <!-- Optional badge -->
        <div class="inline-flex items-center gap-2 glass rounded-full px-4 py-2 text-xs font-semibold text-purple-300 mb-6 border border-purple-500/20">
          Ready to ship?
        </div>
        <h2 class="text-4xl md:text-5xl font-black mb-4">
          CTA Headline<br/><span class="gradient-text">Colored Part</span>
        </h2>
        <p class="text-gray-400 mb-8 max-w-lg mx-auto">Supporting copy.</p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <a href="mailto:hello@glitterlabs.com" class="btn-primary text-white font-semibold px-8 py-4 rounded-full text-sm inline-flex items-center gap-2 justify-center">
            Primary Action
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"/>
            </svg>
          </a>
          <a href="#" class="btn-ghost text-white font-semibold px-8 py-4 rounded-full text-sm inline-flex items-center gap-2 justify-center">
            Secondary Action
          </a>
        </div>
      </div>
    </div>
  </div>
</section>
```

---

## Role Card (Careers)

Full job listing card with description, bullet points, tags, and apply CTA.

```html
<div class="glass card-hover rounded-2xl p-8 border border-white/5">
  <div class="flex flex-col md:flex-row md:items-start md:justify-between gap-6">
    <div class="flex gap-5 items-start">
      <!-- Icon -->
      <div class="w-14 h-14 rounded-xl bg-gradient-to-br from-purple-600/30 to-purple-900/30 border border-purple-500/20 flex items-center justify-center text-2xl shrink-0">🔬</div>
      <div>
        <!-- Title + tags -->
        <div class="flex flex-wrap items-center gap-2 mb-2">
          <h3 class="text-xl font-bold">Role Title</h3>
          <span class="tag">Category</span>
          <span class="tag tag-blue">Full-time</span>
        </div>
        <!-- Description -->
        <div class="text-gray-400 text-sm mb-4 leading-relaxed max-w-2xl">
          Role description paragraph.
        </div>
        <!-- Meta (location, type) -->
        <div class="flex gap-4 mb-4 text-xs text-gray-500">
          <span>📍 Remote</span>
          <span>🕐 Full-time</span>
        </div>
        <!-- Responsibilities -->
        <div class="space-y-1 text-sm text-gray-400">
          <div class="font-medium text-gray-200 mb-2">You'll work on:</div>
          <div class="flex items-start gap-2"><span class="text-purple-400 mt-1">→</span> Responsibility one</div>
          <div class="flex items-start gap-2"><span class="text-purple-400 mt-1">→</span> Responsibility two</div>
          <div class="flex items-start gap-2"><span class="text-purple-400 mt-1">→</span> Responsibility three</div>
        </div>
      </div>
    </div>
    <!-- Apply CTA -->
    <div class="md:shrink-0">
      <a href="mailto:hello@glitterlabs.com?subject=Application: Role Title" class="btn-primary text-white font-semibold px-6 py-3 rounded-full text-sm inline-flex items-center gap-2 whitespace-nowrap">
        Apply Now
        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"/>
        </svg>
      </a>
    </div>
  </div>
</div>
```

**Tag classes:**
```css
.tag        /* Purple */
.tag-blue   /* Blue */
.tag-green  /* Green */
.tag-orange /* Orange */
```

---

## Footer

Consistent 4-column footer used on all pages.

```html
<footer class="border-t border-white/5 py-16 px-6 bg-gray-950">
  <div class="max-w-7xl mx-auto grid grid-cols-1 md:grid-cols-4 gap-10">
    <!-- Brand col (spans 2) -->
    <div class="md:col-span-2">
      <a href="index.html" class="flex items-center gap-2 mb-4">
        <div class="w-8 h-8 rounded-lg bg-gradient-to-br from-purple-500 to-blue-500 flex items-center justify-center text-sm font-black">G</div>
        <span class="text-xl font-black tracking-tight">Glitter Technology Ventures Pvt. Ltd.</span>
      </a>
      <p class="text-gray-400 text-sm leading-relaxed max-w-xs">Company description.</p>
      <!-- Social links -->
      <div class="flex gap-4 mt-6">
        <a href="#" class="glass w-9 h-9 rounded-lg flex items-center justify-center hover:border-purple-500/50 transition-colors text-gray-400 hover:text-white">
          <!-- LinkedIn SVG -->
        </a>
        <a href="#" class="glass w-9 h-9 rounded-lg flex items-center justify-center hover:border-purple-500/50 transition-colors text-gray-400 hover:text-white">
          <!-- X/Twitter SVG -->
        </a>
      </div>
    </div>
    <!-- Quick links -->
    <div>
      <div class="text-sm font-semibold text-gray-200 mb-4">Quick Links</div>
      <ul class="space-y-2 text-sm text-gray-400">
        <li><a href="index.html" class="hover:text-white transition-colors">Home</a></li>
        <li><a href="solutions.html" class="hover:text-white transition-colors">Solutions</a></li>
        <li><a href="about.html" class="hover:text-white transition-colors">About</a></li>
        <li><a href="careers.html" class="hover:text-white transition-colors">Careers</a></li>
      </ul>
    </div>
    <!-- Contact -->
    <div>
      <div class="text-sm font-semibold text-gray-200 mb-4">Contact</div>
      <ul class="space-y-2 text-sm text-gray-400">
        <li><a href="mailto:hello@glitterlabs.com" class="hover:text-white transition-colors">hello@glitterlabs.com</a></li>
      </ul>
    </div>
  </div>
  <!-- Copyright bar -->
  <div class="max-w-7xl mx-auto mt-12 pt-6 border-t border-white/5 flex flex-col md:flex-row items-center justify-between text-xs text-gray-600">
    <span>© 2026 Glitter Technology Ventures Pvt. Ltd.. All rights reserved.</span>
    <span class="mt-2 md:mt-0">Built with AI. Deployed at scale.</span>
  </div>
</footer>
```

---

## Scroll Reveal Animation

Paste this `<script>` block before `</body>` on any page to enable scroll-triggered fade-in for all `section > div` elements.

```html
<script>
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
</script>
```

**Requirement:** Content must be wrapped as `<section><div class="max-w-*">...</div></section>`.

---

## Animated Background Orbs

Decorative gradient blobs for hero backgrounds. Use 2–3 per section.

```html
<!-- Large purple orb (top-left) -->
<div class="absolute top-1/4 left-1/4 w-96 h-96 bg-purple-600/20 rounded-full blur-3xl animate-pulse-slow"></div>

<!-- Medium blue orb (bottom-right, delayed) -->
<div class="absolute bottom-1/4 right-1/4 w-80 h-80 bg-blue-600/20 rounded-full blur-3xl animate-pulse-slow" style="animation-delay:2s"></div>

<!-- Small floating orb (center) -->
<div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-64 h-64 bg-green-500/10 rounded-full blur-3xl animate-float"></div>
```

Requires `animate-pulse-slow` and `animate-float` defined in Tailwind config (see CLAUDE.md).

---

## Gradient Text

Apply to any inline element for the purple → blue → neon gradient.

```html
<span class="gradient-text">Colored Text</span>
```

```css
.gradient-text {
  background: linear-gradient(135deg, #c084fc, #60a5fa, #39FF14);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
```

**Single-color variants (used in Solutions page):**
```html
<!-- Purple only -->
<span style="background: linear-gradient(135deg, #c084fc, #a855f7); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;">Text</span>

<!-- Blue only -->
<span style="background: linear-gradient(135deg, #60a5fa, #3b82f6); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;">Text</span>

<!-- Green only -->
<span style="background: linear-gradient(135deg, #4ade80, #22c55e); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;">Text</span>

<!-- Orange only -->
<span style="background: linear-gradient(135deg, #fb923c, #f97316); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;">Text</span>
```

---

## Neon Status Dot

Pulsing green indicator for "live" status.

```html
<!-- Static -->
<div class="neon-dot"></div>

<!-- Animated -->
<div class="neon-dot animate-pulse"></div>
```

```css
.neon-dot {
  width: 8px; height: 8px;
  background: #39FF14;
  border-radius: 50%;
  box-shadow: 0 0 8px #39FF14;
}
```

---

## Terminal / Live Panel

Decorative "live system" panel — used in the Home page distribution engine section.

```html
<div class="glass rounded-3xl p-8">
  <div class="text-center mb-6">
    <div class="inline-flex items-center gap-2 text-sm font-semibold text-gray-300">
      <div class="neon-dot"></div>
      System Name — Live
    </div>
  </div>
  <div class="space-y-3">
    <!-- Each line = one step in the pipeline -->
    <div class="glass rounded-xl p-3 flex items-center gap-3">
      <div class="w-2 h-2 bg-green-400 rounded-full animate-pulse"></div>
      <span class="text-sm font-mono text-gray-300">agent.action(params) → result</span>
    </div>
    <div class="glass rounded-xl p-3 flex items-center gap-3">
      <div class="w-2 h-2 bg-blue-400 rounded-full animate-pulse" style="animation-delay:0.5s"></div>
      <span class="text-sm font-mono text-gray-300">next_step.run() → approved</span>
    </div>
    <!-- Add more steps as needed -->
  </div>
  <!-- Stats row at bottom -->
  <div class="mt-6 grid grid-cols-3 gap-3 text-center text-xs">
    <div class="glass rounded-lg p-2">
      <div class="text-green-400 font-bold">Metric</div>
      <div class="text-gray-500">label</div>
    </div>
    <!-- Repeat for 3 cols -->
  </div>
</div>
```

**Dot color variants:** `bg-green-400`, `bg-blue-400`, `bg-purple-400`, `bg-yellow-400`

---

## Stats Bar

Horizontal metrics bar between hero and main content.

```html
<section class="py-12 bg-gray-900/50 border-y border-white/5">
  <div class="max-w-6xl mx-auto px-6 grid grid-cols-2 md:grid-cols-4 gap-8 text-center">
    <div>
      <div class="text-4xl font-black" style="background: linear-gradient(135deg, #39FF14, #60a5fa); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;">70%</div>
      <div class="text-gray-400 text-sm mt-1">Metric Label</div>
    </div>
    <!-- Repeat for each stat -->
  </div>
</section>
```

---

## Icon Button

Small square icon button (used for social links in footer).

```html
<a href="#" class="glass w-9 h-9 rounded-lg flex items-center justify-center hover:border-purple-500/50 transition-colors text-gray-400 hover:text-white">
  <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24">
    <!-- SVG path -->
  </svg>
</a>
```

---

## Required CSS Block

Every page needs this `<style>` block in `<head>` alongside the Tailwind CDN:

```css
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap');
* { font-family: 'Inter', sans-serif; }
.glass { background: rgba(255,255,255,0.05); backdrop-filter: blur(16px); border: 1px solid rgba(255,255,255,0.08); }
.glass-dark { background: rgba(0,0,0,0.3); backdrop-filter: blur(16px); border: 1px solid rgba(255,255,255,0.06); }
.gradient-text { background: linear-gradient(135deg, #c084fc, #60a5fa, #39FF14); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
.gradient-bg { background: linear-gradient(135deg, #0f0c29, #302b63, #24243e); background-size: 400% 400%; animation: gradient-x 8s ease infinite; }
.grid-bg { background-image: linear-gradient(rgba(255,255,255,0.03) 1px, transparent 1px), linear-gradient(90deg, rgba(255,255,255,0.03) 1px, transparent 1px); background-size: 50px 50px; }
.card-hover { transition: all 0.3s ease; }
.card-hover:hover { transform: translateY(-6px); box-shadow: 0 20px 60px rgba(168,85,247,0.2); }
.btn-primary { background: linear-gradient(135deg, #9333ea, #3b82f6); transition: all 0.3s ease; }
.btn-primary:hover { background: linear-gradient(135deg, #7e22ce, #2563eb); transform: translateY(-2px); box-shadow: 0 8px 25px rgba(147,51,234,0.4); }
.btn-ghost { border: 1px solid rgba(255,255,255,0.2); transition: all 0.3s ease; }
.btn-ghost:hover { border-color: #a855f7; background: rgba(168,85,247,0.1); transform: translateY(-2px); }
.neon-dot { width: 8px; height: 8px; background: #39FF14; border-radius: 50%; box-shadow: 0 0 8px #39FF14; }
::-webkit-scrollbar { width: 6px; }
::-webkit-scrollbar-track { background: #0a0a0a; }
::-webkit-scrollbar-thumb { background: #9333ea; border-radius: 3px; }
```

And the required Tailwind config:

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
        'gradient-x': {
          '0%, 100%': { 'background-position': '0% 50%' },
          '50%': { 'background-position': '100% 50%' },
        },
        'float': {
          '0%, 100%': { transform: 'translateY(0px)' },
          '50%': { transform: 'translateY(-20px)' },
        },
      },
    },
  },
}
```
