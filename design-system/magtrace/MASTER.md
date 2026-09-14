# Design System Master File

> **LOGIC:** When building a specific page, first check `design-system/pages/[page-name].md`.
> If that file exists, its rules **override** this Master file.
> If not, strictly follow the rules below.

---

**Project:** MAGTRACE
**Generated:** 2026-08-29 18:12:49
**Curated:** 2026-08-29 after Obsidian review and UX research
**Category:** Editorial research / cultural archive explorer

---

## Global Rules

### Color Palette

| Role | Hex | CSS Variable |
|------|-----|--------------|
| Primary | `#191817` | `--color-primary` |
| On Primary | `#FFFFFF` | `--color-on-primary` |
| Secondary | `#69645C` | `--color-secondary` |
| Accent/CTA | `#B64027` | `--color-accent` |
| Background | `#F6F1E8` | `--color-background` |
| Surface | `#FFFDF9` | `--color-surface` |
| Foreground | `#191817` | `--color-foreground` |
| Muted | `#EFE8DD` | `--color-muted` |
| Muted Foreground | `#69645C` | `--color-muted-foreground` |
| Border | `#D8D0C4` | `--color-border` |
| Positive | `#244B3A` | `--color-positive` |
| Destructive | `#DC2626` | `--color-destructive` |
| Ring | `#B64027` | `--color-ring` |

**Color Notes:** Warm paper 60% + ink/surface 30% + accessible vermilion 10%. Vermilion is reserved for the primary CTA, chart focus, links, and annotations. It must not carry meaning without a label or shape.

### Typography

- **Heading Font:** Noto Serif JP (Bold)
- **Body/UI Font:** Noto Sans JP (Regular / Medium / Bold)
- **Mood:** Japanese editorial, cultural archive, trustworthy research, readable data
- **Rules:** Body 16px minimum; captions 12–14px only for non-critical metadata; body line-height 1.6–1.75; Japanese line length 35–50 characters.

**CSS Import:**
```css
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;500;700&family=Noto+Serif+JP:wght@600;700&display=swap');
```

### Spacing Variables

| Token | Value | Usage |
|-------|-------|-------|
| `--space-xs` | `4px` / `0.25rem` | Tight gaps |
| `--space-sm` | `8px` / `0.5rem` | Icon gaps, inline spacing |
| `--space-md` | `16px` / `1rem` | Standard padding |
| `--space-lg` | `24px` / `1.5rem` | Section padding |
| `--space-xl` | `32px` / `2rem` | Large gaps |
| `--space-2xl` | `48px` / `3rem` | Section margins |
| `--space-3xl` | `64px` / `4rem` | Hero padding |

### Shadow Depths

| Level | Value | Usage |
|-------|-------|-------|
| `--shadow-sm` | `0 1px 2px rgba(0,0,0,0.05)` | Subtle lift |
| `--shadow-md` | `0 4px 6px rgba(0,0,0,0.1)` | Cards, buttons |
| `--shadow-lg` | `0 10px 15px rgba(0,0,0,0.1)` | Modals, dropdowns |
| `--shadow-xl` | `0 20px 25px rgba(0,0,0,0.15)` | Hero images, featured cards |

---

## Component Specs

### Buttons

```css
/* Primary Button */
.btn-primary {
  background: #191817;
  color: white;
  padding: 12px 24px;
  border-radius: 8px;
  font-weight: 600;
  transition: all 200ms ease;
  cursor: pointer;
}

.btn-primary:hover {
  opacity: 0.9;
  transform: translateY(-1px);
}

/* Secondary Button */
.btn-secondary {
  background: transparent;
  color: #191817;
  border: 1px solid #191817;
  padding: 12px 24px;
  border-radius: 8px;
  font-weight: 600;
  transition: all 200ms ease;
  cursor: pointer;
}
```

### Cards

```css
.card {
  background: #FFFDF9;
  border-radius: 12px;
  padding: 24px;
  border: 1px solid #D8D0C4;
  box-shadow: var(--shadow-sm);
  transition: all 200ms ease;
  cursor: pointer;
}

.card:hover {
  border-color: #69645C;
}
```

### Inputs

```css
.input {
  padding: 12px 16px;
  border: 1px solid #D8D0C4;
  border-radius: 8px;
  font-size: 16px;
  transition: border-color 200ms ease;
}

.input:focus {
  border-color: #B64027;
  outline: none;
  box-shadow: 0 0 0 3px rgba(182, 64, 39, 0.2);
}
```

### Modals

```css
.modal-overlay {
  background: rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(4px);
}

.modal {
  background: white;
  border-radius: 16px;
  padding: 32px;
  box-shadow: var(--shadow-xl);
  max-width: 500px;
  width: 90%;
}
```

---

## Style Guidelines

**Style:** Japanese editorial × Swiss information design

**Keywords:** content-first, 12-column grid, restrained asymmetry, warm paper, direct annotation, quiet tactility, clear provenance

**Best For:** magazine archives, cultural discovery, research tools, museum-like exploration

**Key Effects:** display: grid, grid-template-columns: repeat(12 1fr), gap: 1rem, mathematical ratios, clear hierarchy

### Page Pattern

**Pattern Name:** Search → insight → evidence → next exploration

- **Primary task:** Search one term and understand one defensible cultural change.
- **CTA placement:** One primary search action; secondary actions are compare, share, and open source.
- **Home order:** Search → featured discovery → topic trails → trust/provenance.
- **Analysis order:** editorial takeaway → time range/filter → annotated line chart → related-context trail → representative articles → methodology.
- **State order:** loading skeleton → partial result/cached result → empty with query suggestions → error with retry.

---

## Anti-Patterns (Do NOT Use)

- ❌ Poor typography
- ❌ Slow loading
- ❌ Generic dashboard with equal-weight cards
- ❌ Decorative graphs without a one-sentence takeaway
- ❌ Bar charts for dense continuous time series
- ❌ Placeholder-only search labels
- ❌ Tiny mobile metadata below 12px or touch targets below 44px
- ❌ Success-state-only mockups

### Additional Forbidden Patterns

- ❌ **Emojis as icons** — Use SVG icons (Heroicons, Lucide, Simple Icons)
- ❌ **Missing cursor:pointer** — All clickable elements must have cursor:pointer
- ❌ **Layout-shifting hovers** — Avoid scale transforms that shift layout
- ❌ **Low contrast text** — Maintain 4.5:1 minimum contrast ratio
- ❌ **Instant state changes** — Always use transitions (150-300ms)
- ❌ **Invisible focus states** — Focus states must be visible for a11y

---

## Pre-Delivery Checklist

Before delivering any UI code, verify:

- [ ] No emojis used as icons (use SVG instead)
- [ ] All icons from consistent icon set (Heroicons/Lucide)
- [ ] `cursor-pointer` on all clickable elements
- [ ] Hover states with smooth transitions (150-300ms)
- [ ] Light mode: text contrast 4.5:1 minimum
- [ ] Focus states visible for keyboard navigation
- [ ] `prefers-reduced-motion` respected
- [ ] Responsive: 375px, 768px, 1024px, 1440px
- [ ] No content hidden behind fixed navbars
- [ ] No horizontal scroll on mobile
