# Omnipotent — Design Philosophy

The visual identity of Omnipotent blends a dark sovereign aesthetic with clear information hierarchy. This document captures the merged design system used across the marketing site, CLI output, and documentation.

---

## Design Lineage

Two influences converge:

1. **Sovereign Dark Theme** — The original Omnipotent identity. Deep voids, gold accents, glassmorphism, monospace typography. Communicates authority and control.
2. **iloom.ai Engagement Funnel** — Centered massive typography, question-based hero hooks, terminal demos, persona cards, clean benefit grids. Communicates accessibility and momentum.

The result: a site that feels like a command center, not a SaaS landing page.

---

## Color Tokens

| Token | Value | Usage |
|-------|-------|-------|
| `--void` | `#000000` | True black backgrounds |
| `--abyss` | `#0A0F14` | Primary page background |
| `--surface-raised` | `#1E293B` | Cards, panels |
| `--surface-overlay` | `#2D3748` | Hover states |
| `--surface-subtle` | `rgba(30,41,59,0.2)` | Soft card backgrounds |
| `--surface-terminal` | `rgba(0,0,0,0.6)` | Terminal window bg |
| `--sovereign-gold` | `#FFD700` | Primary accent — sovereignty, authority |
| `--gold-muted` | `#D4A843` | Borders, subtle gold |
| `--gold-warm` | `#E0B850` | Hover gold |
| `--cyan` | `#00D4FF` | Secondary accent — technology, links |
| `--matrix-green` | `#00FF00` | Tertiary accent — success, active states |
| `--text-primary` | `#E0E0E0` | Body text |
| `--text-secondary` | `#94A3B8` | Muted text, descriptions |
| `--glass-edge` | `rgba(0,212,255,0.3)` | Glass panel borders |
| `--glass-bg` | `rgba(30,41,59,0.45)` | Glass panel backgrounds |
| `--glass-bg-hover` | `rgba(30,41,59,0.65)` | Glass panel hover |

### Three-Color Accent System

- **Gold** = Sovereignty, ownership, authority
- **Cyan** = Technology, connectivity, intelligence
- **Green** = Growth, success, active/running states

Every card, badge, and border accent uses one of these three. They rotate in left-border accents on benefit cards and persona badges.

---

## Typography

| Role | Font | Weight | Usage |
|------|------|--------|-------|
| Display | Inter | 800-900 | Hero headlines |
| Heading | Inter | 600-700 | Section headings |
| Body | Inter | 400-500 | Paragraph text |
| Code | JetBrains Mono | 400-700 | Terminal, code blocks, CLI output |

### Scale

```
h1: clamp(2.8rem, 2.2rem + 3vw, 4.5rem)  — Hero only
h2: clamp(1.6rem, 1.2rem + 2vw, 2.6rem)  — Section headings
h3: 1.1rem                                 — Card titles
body: 0.92rem                              — Base text
small: 0.78-0.85rem                        — Captions, citations
mono: 0.8rem                               — Code blocks
```

Loaded via Google Fonts: `Inter:wght@400;500;600;700;800;900` + `JetBrains+Mono:wght@400;500;600;700`.

---

## Layout Principles

1. **Centered sections** — All content flows through `max-width: 1120px` containers with generous padding.
2. **Alternating backgrounds** — Sections alternate between `--abyss` and `rgba(255,255,255,0.015)` for visual rhythm.
3. **Section anatomy** — Every section has: label (uppercase monospace), heading, optional subheading, content.
4. **Vertical rhythm** — `--space-*` scale from 4px to 80px. Sections get 80px vertical padding (48px on mobile).
5. **Mobile-first** — Single column below 720px, multi-column above. Hero adjusts via `clamp()`.

---

## Card Patterns

### Benefit Card
- Left-border accent (3px, one of gold/cyan/green)
- Glass background (`rgba(30,41,59,0.2)`)
- Icon + title + description
- Hover: border brightens, card lifts 2px

### Persona Card
- Colored badge (gold/cyan/green) with role label
- Bold headline + lead paragraph + body
- Same glass background pattern

### Legion Card
- Compact horizontal layout: sigil (circle with initial) + name + role
- 4-column grid on desktop, 2-column on tablet, 1-column on mobile
- Sigil colors map to agent tier (gold=supervisor, cyan=legion, gray=execution)

### Documentation Link Card
- Horizontal: icon circle + title + description
- Icon circle uses the three-color system
- Hover lifts and adds cyan border glow

---

## Spacing System

```
--space-1:   4px
--space-2:   8px
--space-3:  12px
--space-4:  16px
--space-5:  20px
--space-6:  24px
--space-8:  32px
--space-10: 40px
--space-12: 48px
--space-16: 64px
--space-20: 80px
```

---

## Animation Rules

1. **Scroll reveal** — Elements start `opacity: 0; transform: translateY(24px)` and reveal on intersection (threshold 0.12).
2. **Staggered delays** — Each sibling gets +60ms delay via `--sr-delay` CSS custom property.
3. **Easing** — `cubic-bezier(0.16, 1, 0.3, 1)` for sovereign feel (fast start, gentle land).
4. **Duration** — Fast: 200ms, Normal: 350ms, Slow: 600ms.
5. **Terminal lines** — Appear line-by-line with `transition-delay` per line, triggered by IntersectionObserver.
6. **Reduced motion** — All animations disabled when `prefers-reduced-motion: reduce` is active. Elements receive `.visible` class immediately.

---

## Engagement Funnel Pattern

The page follows a deliberate narrative arc:

```
1. Hero          — Question hook + install CTA (capture intent)
2. Trust Bar     — Technology credibility (build confidence)
3. Terminal Demo — "See it work" (reduce uncertainty)
4. Benefits Grid — Why this matters (communicate value)
5. Legion Grid   — Meet the agents (make it tangible)
6. Getting Started — Three steps to install (reduce friction)
7. Documentation — Deep dive links (serve advanced users)
8. Persona Cards — "Is this for me?" (qualify the reader)
9. Philosophy    — The deeper story (create emotional connection)
10. FAQ          — Handle objections (remove blockers)
11. Newsletter   — Capture leads (convert interest)
12. Footer       — Navigation + attribution
```

Each section has exactly one job. No section tries to do two things.

---

## Accessibility

- All sections have `aria-labelledby` pointing to their heading
- SVG icons use `aria-hidden="true"`
- FAQ uses native `<details>/<summary>` (keyboard accessible by default)
- Focus indicators follow the cyan accent color
- Color contrast ratios exceed WCAG AA for all text-on-background combinations
- `prefers-reduced-motion` fully supported
- `prefers-color-scheme` not needed (dark-only by design intent)
