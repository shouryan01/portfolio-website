# Design Engine & Visual Philosophy Guide

A reusable design system and aesthetic standard distilled from **Taste** (anti-slop constraints), **Impeccable** (craft & micro-details), and **UI/UX Pro Max** (ergonomics & accessibility).

---

## 1. Anti-Slop: What NOT to Do (Taste Filter)

Most AI-generated and template interfaces fail because they stack identical, predictable tropes. Avoid these defaults:

- ❌ **No generic purple/indigo accents or blue-to-purple hero gradients** (the #1 AI giveaway).
- ❌ **No `bg-clip-text` gradient headlines** across hero banners.
- ❌ **No Inter-only monoculture** (or relying solely on Geist / Space Grotesk / Arial as your entire identity).
- ❌ **No uniform `rounded-2xl`** slapped indiscriminately on every card, modal, and button.
- ❌ **No glowing aurora blobs**, neon radial gradients, or identical glow shadows behind every card.
- ❌ **No cookie-cutter 3-card feature grid** with an identical rounded icon square.
- ❌ **No vague 10-word, 56px headlines** that say nothing concrete.
- ❌ **No Bento grids by default** unless the information genuinely benefits from asymmetric spatial organization.
- ❌ **No low-contrast gray text** (`text-gray-400` / `text-gray-500` on white backgrounds).
- ❌ **No `hover:scale-105`** bounce on every interactive surface.
- ❌ **No emoji bullets** as feature icons (🚀 ⚡ ✨ 🎯 💡).
- ❌ **No glassmorphism blur overload** (`backdrop-blur-xl` + translucent borders everywhere).

---

## 2. Typography & Editorial Hierarchy

Treat typography like print typography: intentional, rhythmic, and content-driven.

### The Editorial Trinity

Pair distinct font classifications with clear roles:

1. **Editorial Serif (`--font-serif`):** Use for headlines, pull-quotes, and section titles. Select optical-sized serifs with expressive italics (e.g., _Newsreader_, _Fraunces_, _Lora_, _Playfair Display_).
2. **Contemporary Geometric Sans (`--font-sans`):** Use for body copy, navigational links, and UI labels (e.g., _Plus Jakarta Sans_, _General Sans_, _Satoshi_).
3. **Engineered Monospace (`--font-mono`):** Use for metadata, tags, status pills, numbers, and code blocks (e.g., _JetBrains Mono_, _Geist Mono_).

### Hierarchy Rules

- Contrast scale with weight: A light/normal italic serif headline paired with a crisp medium-weight sans kicker and mono metadata creates authentic editorial presence.
- Avoid tracking out lowercase body text. Only apply slight positive letter-spacing (`tracking-wider` or `0.05em`) to uppercase micro-labels.
- Maintain readable measure (line length): 45–75 characters per line (`max-w-prose` or `max-w-2xl`).

---

## 3. Color Architecture & Neutral Palette

Avoid sterile cool grays (`#64748b` slate) and yellowed cream slop (`#faf8f4`). Build layered, warm stone and obsidian depth.

### Token Layering Schema

Always separate your semantic layers into CSS variables:

| Token Name           | Light Mode Value       | Dark Mode Value            | Purpose                      |
| :------------------- | :--------------------- | :------------------------- | :--------------------------- |
| `--background`       | `#fafaf9` (Warm Stone) | `#0c0a09` (Obsidian Pitch) | Canvas background            |
| `--surface-elevated` | `#ffffff`              | `#1c1917` (Warm Graphite)  | Cards, popovers, modals      |
| `--surface-muted`    | `#f5f5f4`              | `#171513`                  | Pill tags, input backgrounds |
| `--surface-subtle`   | `#e7e5e4`              | `#292524`                  | Hover states, active fills   |
| `--border`           | `#e7e5e4`              | `#292524`                  | 1px hairline boundary        |
| `--border-hover`     | `#d6d3d1`              | `#44403c`                  | Interactive border hover     |
| `--text-primary`     | `#1c1917` (Deep Ink)   | `#f5f5f4` (Crisp Chalk)    | High-contrast readability    |
| `--text-secondary`   | `#57534e` (Warm Slate) | `#a8a29e` (Muted Zinc)     | Subheadings, body copy       |
| `--text-tertiary`    | `#8c8883`              | `#78716c`                  | Metadata, timestamps         |
| `--accent`           | `#292524`              | `#fafaf9`                  | Primary actions & badges     |

---

## 4. Craft & Micro-Details (Impeccable Standard)

- **Hairline Borders:** Use crisp `1px` borders (`border-border`) rather than heavy drop shadows to define surfaces.
- **Surface Elevation via Tone, Not Shadow:** In dark mode, elevation is expressed through slightly lighter surface tones (`--surface-elevated`), not drop shadows.
- **Tactile Transitions:** Keep transitions short and snappy: `transition-colors duration-150` or `ease-out duration-200`. Avoid bouncy elastic springs.
- **Zero Hydration Flash:** Always handle client-only theme mounting cleanly using `useSyncExternalStore` or `suppressHydrationWarning` on `<html>`.

---

## 5. Ergonomics & Accessibility (UI/UX Pro Max)

- **Contrast Ratios:** Ensure primary body text and interactives meet WCAG AAA (minimum 7:1 for normal text against its surface).
- **Interactive Targets:** Every clickable target must have a minimum touch target of 36×36px (preferably 44×44px on mobile).
- **Focus Rings:** Never strip `outline: none` without providing an explicit, high-contrast replacement:
  ```css
  focus-visible: outline-2 focus-visible: outline-offset-2 focus-visible: outline-accent;
  ```
- **Motion Accessibility:** Respect reduced-motion preferences:
  ```css
  @media (prefers-reduced-motion: reduce) {
    * {
      animation-duration: 0.01ms !important;
      transition-duration: 0.01ms !important;
    }
  }
  ```
- **Semantic Structure:** Always use standard landmarks (`<header>`, `<main>`, `<nav>`, `<footer>`) and accessible button labels (`aria-label` with descriptive text).
