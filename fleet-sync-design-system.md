# Honda Fleet Sync — Design System

**Version:** 1.0  
**Last Updated:** May 2026  
**Platform:** iOS (Mobile-first)  
**Author:** Souvik B.

---

## 1. Design Principles

This design system governs the Honda Fleet Sync driver-facing logistics app. Every decision should reinforce these principles:

**Clarity over decoration.** Drivers interact with the app in motion, often one-handed, in varying lighting. Every element must communicate instantly. No ambiguity.

**Scannable hierarchy.** Information is structured so drivers can glance, not read. Numbers are bold. Labels are muted. Status is color-coded.

**Minimal cognitive load.** One primary action per screen. Progressive disclosure via bottom sheets and accordions. Never overwhelm.

**Brand alignment.** Honda's identity is precision and reliability. The red is used sparingly — only for primary actions and active states. The UI is clean, structured, and confident.

**Accessibility-first.** Minimum 4.5:1 contrast for body text. Touch targets ≥44×44pt. No information conveyed by color alone — always paired with text or icons.

---

## 2. Design Tokens

Design tokens are the atomic values that ensure consistency across every screen. They replace hardcoded values everywhere.

### 2.1 Color Tokens

#### Primitive Tokens (Raw Values)

These are the raw hex values. Never use these directly in components — always reference semantic tokens.

| Token Name | Hex | Swatch |
|---|---|---|
| `color.red.500` | `#E60012` | Honda Red |
| `color.red.600` | `#D00011` | Red Hover/Pressed |
| `color.red.700` | `#C8000F` | Red Deep Press |
| `color.red.50` | `#FEF0F0` | Red Tint |
| `color.green.500` | `#2EAD4B` | Success Green |
| `color.green.600` | `#2E7D32` | Success Dark |
| `color.green.50` | `#F0FFF4` | Success Tint |
| `color.green.100` | `#E8F5E9` | Success Light |
| `color.yellow.500` | `#D97706` | Warning Amber |
| `color.yellow.50` | `#FFF8E1` | Warning Tint |
| `color.yellow.border` | `#EED44A` | Warning Border |
| `color.neutral.900` | `#1A1A1A` | Ink/Primary Text |
| `color.neutral.700` | `#666666` | Muted Text |
| `color.neutral.500` | `#777777` | Disabled/Placeholder |
| `color.neutral.400` | `#BBBBBB` | Inactive Icons |
| `color.neutral.300` | `#CCCCCC` | Light Borders |
| `color.neutral.200` | `#E4E5E8` | Dividers |
| `color.neutral.100` | `#F5F5F7` | Surface/Tile |
| `color.neutral.75` | `#F7F7F9` | Page Background |
| `color.neutral.50` | `#FAFAFA` | Subtle Surface |
| `color.white` | `#FFFFFF` | White |
| `color.indigo.500` | `#4F46E5` | Info/Accent |
| `color.indigo.50` | `#EEF2FF` | Info Tint |

#### Semantic Tokens (Usage-Mapped)

Map primitives to purpose. These are what components reference.

| Semantic Token | Maps To | Usage |
|---|---|---|
| `color.brand.primary` | `color.red.500` | Primary CTAs, active nav tab, key UI accents |
| `color.brand.primary.hover` | `color.red.600` | Hover/pressed state of primary elements |
| `color.brand.primary.tint` | `color.red.50` | Light background behind red elements, error surface |
| `color.text.primary` | `color.neutral.900` | Headings, values, primary body text |
| `color.text.secondary` | `color.neutral.700` | Labels, descriptions, supporting text |
| `color.text.disabled` | `color.neutral.500` | Placeholder text, inactive labels (4.5:1 contrast on white) |
| `color.text.inverse` | `color.white` | Text on dark/red backgrounds |
| `color.surface.primary` | `color.white` | Cards, sheets, main content areas |
| `color.surface.secondary` | `color.neutral.100` | Tile backgrounds, input fills, section bg |
| `color.surface.page` | `color.neutral.75` | Page-level background behind cards |
| `color.border.default` | `color.neutral.200` | Card borders, dividers, separators |
| `color.border.subtle` | `color.neutral.100` | Inner row separators |
| `color.status.success` | `color.green.500` | Confirmed, delivered, completed |
| `color.status.success.tint` | `color.green.50` | Success banner background |
| `color.status.warning` | `color.yellow.500` | Delayed, attention needed |
| `color.status.warning.tint` | `color.yellow.50` | Warning banner background |
| `color.status.error` | `color.red.500` | Failed, issue reported |
| `color.status.error.tint` | `color.red.50` | Error banner background |
| `color.status.info` | `color.indigo.500` | Informational badges |
| `color.status.info.tint` | `color.indigo.50` | Info banner background |

#### Color Usage Rules

**Red (#E60012) — Use sparingly.** Only for: primary action buttons, active bottom nav tab, selected state indicators, and urgent status. Never for body text, backgrounds larger than a badge, or decorative elements. Red means "act now" in this system.

**Green (#2EAD4B) — Success and confirmation only.** Delivered badges, scan-confirmed banners, completed states. Never as a general accent. Always pair green status with text label — do not rely on color alone.

**Yellow/Amber (#D97706) — Warning and attention.** Delayed orders, requires-action states. Always use the tint background with a visible border for banner patterns.

**Neutral grays — The workhorse.** The majority of the UI is gray-scale. This keeps red impactful when it appears. Use the scale consistently: 900 for headings, 700 for labels, 500 for placeholders, 200 for borders.

#### Accessibility Notes

| Pair | Contrast Ratio | WCAG AA |
|---|---|---|
| `#1A1A1A` on `#FFFFFF` | 16.8:1 | Pass |
| `#666666` on `#FFFFFF` | 5.7:1 | Pass |
| `#777777` on `#FFFFFF` | 4.5:1 | Pass |
| `#E60012` on `#FFFFFF` | 4.6:1 | Pass (barely — avoid for small text below 14px) |
| `#FFFFFF` on `#E60012` | 4.6:1 | Pass for button text at 10px+ bold weight |
| `#2E7D32` on `#FFFFFF` | 4.8:1 | Pass |

**Note:** Green text labels (e.g., "Delivered") use the darker `#2E7D32` to meet WCAG AA. The lighter `#2EAD4B` is reserved for icons, badges, and filled elements where the surface area is large enough.

---

### 2.2 Typography Tokens

**Font Family:** Inter (Google Fonts)  
**Weights available:** 400 (Regular), 500 (Medium), 600 (SemiBold), 700 (Bold), 800 (ExtraBold)

#### Type Scale

| Token | Size | Weight | Line Height | Usage |
|---|---|---|---|---|
| `type.display` | 22px | 800 | 1.2 | Hero stats, large dashboard numbers |
| `type.heading.lg` | 17px | 700 | 1.3 | Screen titles, section headers (used sparingly) |
| `type.heading.md` | 16px | 600–700 | 1.3 | Top bar title |
| `type.heading.sm` | 14px | 700 | 1.35 | Card titles, section labels |
| `type.body.lg` | 13px | 500–600 | 1.4 | Emphasized body content |
| `type.body.md` | 12px | 500–600 | 1.4 | Standard card content, descriptions |
| `type.body.sm` | 11px | 400–500 | 1.4 | Secondary info, status bar |
| `type.caption.lg` | 10px | 600–700 | 1.3 | Button labels, tag text, tile labels |
| `type.caption.md` | 9px | 500–600 | 1.3 | Metadata, timestamps, badge text |
| `type.caption.sm` | 8px | 400–600 | 1.3 | Row labels, fine print, data table cells |
| `type.micro` | 7.5px | 500 | 1.2 | Scanner hints, ultra-compact labels |

#### Typography Rules

**Never go below 8px for any readable text.** The 7.5px micro token exists solely for non-essential scanner hints — do not use it elsewhere.

**Strict mapping:** Every component type maps to exactly one token from the scale above. Card titles always use `type.heading.sm` (14px/700). Button labels always use `type.caption.lg` (10px/700). No ad-hoc sizes.

**Weight discipline:** Use a maximum of 3 weights per screen to maintain hierarchy clarity: 400 for body, 600 for emphasis, 700 for headings.

---

### 2.3 Spacing Tokens

The system uses a **4px base unit** with an 8px primary rhythm.

| Token | Value | Usage |
|---|---|---|
| `space.xs` | 4px | Tight gaps (icon-to-text inline, badge padding) |
| `space.sm` | 6px | Inner padding for compact elements, small gaps |
| `space.md` | 8px | Standard gap between related elements, tile gaps |
| `space.lg` | 12px | Card internal padding, section gaps, component margins |
| `space.xl` | 14px | Screen horizontal padding (left/right content inset) |
| `space.2xl` | 16px | Section spacing, footer/header padding, sheet body padding |
| `space.3xl` | 20px | Large section breaks |
| `space.4xl` | 24px | Sheet footer padding, major separations |

#### Spacing Rules

**Horizontal screen padding:** `14px` on all screens, no exceptions.

**Vertical gaps:** `12px` (`space.lg`) between sibling components. `16px` (`space.2xl`) between major sections.

**Card inner padding:** `12px` on all sides for every card and container.

---

### 2.4 Border & Radius Tokens

| Token | Value | Usage |
|---|---|---|
| `radius.sm` | 4px | Tags, small badges, inner elements |
| `radius.md` | 8px | Cards, buttons, inputs, tiles — **primary radius** |
| `radius.lg` | 12px | Bottom sheets (top corners), modal cards |
| `radius.xl` | 20px | Bottom sheet top corners on some screens |
| `radius.full` | 50% / 9999px | Avatar circles, round icon buttons |
| `border.default` | 1px solid `color.border.default` | Standard card/component border |
| `border.strong` | 1.5px solid `color.border.default` | Emphasized card borders |
| `border.active` | 1.5px solid `color.brand.primary` | Selected/active state border |



---

### 2.5 Shadow Tokens

| Token | Value | Usage |
|---|---|---|
| `shadow.sheet` | `0 -4px 20px rgba(0,0,0,0.15)` | Bottom sheets sliding up |
| `shadow.card` | `0 8px 24px rgba(0,0,0,0.13)` | Elevated cards, floating elements |
| `shadow.success` | `0 6px 20px rgba(46,173,75,0.30)` | Success state glow |
| `shadow.overlay` | `0 4px 20px rgba(0,0,0,0.40)` | Nav panel overlay |

---

### 2.6 Motion Tokens

| Token | Value | Usage |
|---|---|---|
| `motion.fast` | 150ms | Button press feedback, icon state changes |
| `motion.normal` | 250ms | Accordion expand/collapse, fade transitions |
| `motion.slow` | 400ms | Bottom sheet slide, page transitions |
| `motion.easing.default` | `cubic-bezier(0.4, 0, 0.2, 1)` | Standard Material-style easing |
| `motion.easing.spring` | `cubic-bezier(0.32, 0.72, 0, 1)` | Playful/bouncy elements |
| `motion.easing.ease-out` | `ease-out` | Exit animations, slide-up sheets |

#### Motion Rules

**Always provide `prefers-reduced-motion` support.** Wrap all animations in a media query that disables or reduces them when the user has this setting enabled.

**Button press:** Use `transform: scale(0.98)` on `:active` with `motion.fast` timing. This is already consistent.

**Bottom sheets:** Slide from bottom using `transform: translateY(100%)` → `translateY(0)` with `motion.slow` and `motion.easing.default`.

**Accordions:** `max-height` transition with `motion.normal` and `motion.easing.default`. Pair with opacity fade.

---

## 3. Component Library

### 3.1 Buttons

#### Primary Button

- **Background:** `color.brand.primary` (#E60012)
- **Text:** `color.text.inverse` (#FFFFFF), `type.caption.lg` (10px/700)
- **Border:** none (or 1.5px solid matching background)
- **Radius:** `radius.md` (8px)
- **Visual height:** 32px
- **Touch target:** 44px minimum (extend via padding around the visual element)
- **States:** Default → Hover (`color.brand.primary.hover`) → Pressed (scale 0.98) → Disabled (opacity 0.5)

#### Secondary Button (Outline)

- **Background:** `color.surface.primary` (#FFFFFF)
- **Text:** `color.brand.primary` (#E60012), `type.caption.lg` (10px/700)
- **Border:** 1.5px solid `color.brand.primary`
- **Radius:** `radius.md` (8px)
- **Visual height:** 32px
- **Touch target:** 44px minimum
- **States:** Default → Hover (tint background) → Pressed (scale 0.98)

#### Link Button

- **Background:** none
- **Text:** `color.brand.primary`, `type.caption.sm` (8px/600)
- **Decoration:** underline, `text-underline-offset: 2px`

#### Icon Button (Circle)

- **Visual size:** 24px diameter
- **Touch target:** 44px minimum (10px invisible padding around the visual circle)
- **Border:** 1px solid `color.brand.primary`
- **Icon:** 11px, fill `color.brand.primary`
- **Radius:** `radius.full`
- **Accessibility:** Must include `aria-label` describing the action (e.g., "Call recipient", "Send message")

---

### 3.2 Cards

#### Standard Card

- **Background:** `color.surface.primary`
- **Border:** `border.default` or `border.strong`
- **Radius:** `radius.md`
- **Padding:** `space.lg` (12px)
- **Header:** Title left (`type.heading.sm`), action buttons right
- **Rows:** Label-value pairs, `type.caption.sm` (8px), separated by `border.subtle` bottom lines

#### Stat Tile

- **Background:** `color.surface.primary`
- **Border:** `border.default`
- **Radius:** `radius.md`
- **Padding:** `space.md` (8px)
- **Layout:** Vertical — icon/metric top, label bottom
- **Metric:** `type.display` or `type.heading.lg`, color varies by type
- **Label:** `type.caption.sm`, `color.text.secondary`

---

### 3.3 Bottom Sheet

- **Overlay:** `rgba(0,0,0,0.48)` (`#0000007A`)
- **Sheet background:** `color.surface.primary`
- **Top corners:** `radius.xl` (20px) — standardize this
- **Shadow:** `shadow.sheet`
- **Header:** Title centered (`type.heading.md`), close button (X) top-right
- **Close button:** 24px, `color.text.secondary`, circle or bare icon
- **Animation:** Slide up from bottom, `motion.slow`, `motion.easing.default`
- **Footer:** Sticky bottom with primary CTA button, padding `space.4xl` (24px) horizontal

---

### 3.4 Navigation

#### Top Bar

- **Height:** ~36–44px (including status bar clearance)
- **Background:** `color.surface.primary`
- **Border:** 1px solid `color.border.default` (bottom)
- **Title:** `type.heading.md` (16px/600), centered
- **Left action:** Hamburger menu (3 bars, 3px gap, `color.text.primary`)
- **Right action:** Icon buttons (notifications bell, etc.)

#### Bottom Navigation Bar

- **Height:** 64px
- **Background:** `color.surface.primary`
- **Border:** 1px solid `color.border.default` (top)
- **Tabs:** 4 items max (Home, Orders, Diagnostics, Profile)
- **Tab layout:** Icon (20px, stroke 1.8px) + label (`type.caption.md`, 9.5px)
- **Active state:** Icon stroke `color.brand.primary`, label `color.brand.primary` (600 weight)
- **Inactive state:** Icon stroke `#777`, label `#777` (400 weight)

---

### 3.5 Status Badges

| Status | Background | Text Color | Border |
|---|---|---|---|
| Delivered | `color.status.success.tint` | `color.status.success` | none |
| In Transit | `color.status.info.tint` | `color.status.info` | none |
| Delayed | `color.status.warning.tint` | `color.status.warning` | `color.yellow.border` |
| Failed | `color.status.error.tint` | `color.status.error` | none |

- **Radius:** `radius.sm` (4px)
- **Padding:** 3px 8px
- **Text:** `type.caption.md` (9px/600)
- **Rule:** Always pair badge color with text label. Never rely on color alone.

---

### 3.6 Search Input

- **Height:** 30px
- **Background:** `color.surface.secondary` (#F5F5F7)
- **Border:** 1px solid `color.border.default`
- **Radius:** `radius.md` (8px)
- **Padding:** 0 10px 0 30px (left space for search icon)
- **Text:** `type.body.sm` (11px/400)
- **Placeholder:** `color.text.disabled` (#777)
- **Icon:** Search magnifier, 12px, `color.text.secondary`

---

### 3.7 Accordion / Expandable Section

- **Container:** `border.default`, `radius.md`
- **Header:** Tappable full-width, padding `space.lg` (12px), with chevron right
- **Chevron:** 10px, rotates 180° on open, `motion.normal` timing
- **Body:** `max-height: 0` → `max-height: 260px` with `motion.easing.default`
- **Body padding:** `space.lg` (12px)
- **Divider:** 1px `color.border.default` between header and body on open

---

### 3.8 Scanner / Barcode UI

- **Scanner area:** Full-width, 150px height, dark background (#1A1A1A)
- **Scan frame:** 180×80px, 1.5px border `color.brand.primary`, `radius.sm` (5px)
- **Scan line:** 1.5px height, `color.brand.primary`, animated sweep (2s ease-in-out infinite)
- **Hint text:** `type.micro` (8px), `#888`, centered below frame

---

### 3.9 Proof of Delivery Tiles

- **Layout:** Horizontal row, 3 tiles, equal width (`flex: 1`)
- **Border:** `border.strong`
- **Radius:** `radius.md`
- **Padding:** 8px vertical, 4px horizontal
- **Icon:** 16px, stroke `color.text.primary`, stroke-width 1.8, no fill
- **Label:** `type.caption.sm` (8px/600)
- **Press state:** Background → `color.surface.secondary`, scale 0.98

---

### 3.10 Attachment Row

- **Background:** `#F0F0F0`
- **Radius:** `radius.md`
- **Padding:** 9px 12px
- **Text:** `type.caption.md` (9px/500)
- **Delete button:** Trash icon, 14px, stroke `color.text.secondary`
- **Entry animation:** Fade in + translateY(6px → 0), `motion.normal`

---

## 4. Iconography

**Style:** Outline/stroke-based (not filled)  
**Stroke width:** 1.8px (consistent across all icons)  
**Default color:** `color.text.primary` (#1A1A1A) or `color.text.secondary` (#666)  
**Active color:** `color.brand.primary` (#E60012) — stroke only, no fill  
**Sizes:** 12px (inline), 16px (tiles/compact), 20px (nav bar), 24px (action buttons)

**Rules:**
- Never mix filled and outline icons at the same hierarchy level
- All icons must have `stroke-linecap: round` and `stroke-linejoin: round` for consistency
- Icon-only buttons must have an `aria-label` for accessibility
- Maintain consistent optical sizing — a 20px circle icon and a 20px square icon should feel the same visual weight

---

## 5. Layout Patterns

### Screen Structure

Every screen follows this vertical stack:

```
┌─────────────────────┐
│    Status Bar (36px) │  Fixed
├─────────────────────┤
│    Top Bar (44px)    │  Fixed
├─────────────────────┤
│                     │
│    Scrollable       │  flex: 1, overflow-y: auto
│    Content Area     │
│                     │
├─────────────────────┤
│  Bottom Nav (64px)  │  Fixed (or Footer CTA)
└─────────────────────┘
```

### Content Padding

- **Horizontal:** 14px left and right (standardized)
- **Vertical between components:** 12px
- **Vertical between sections:** 16px
- **Card internal padding:** 12px all sides

### Grid

No formal column grid — the app uses a single-column layout with full-width cards and a 2-column tile grid for stat tiles (using `flex`, equal width, 8px gap).

---

## 6. Patterns & Interaction Guidelines

### Progressive Disclosure

The app uses a layered disclosure pattern: Home screen → Bottom sheet (order selection) → Bottom sheet (route selection) → Full screen (verification) → Completion screen. Each step reveals only what's needed for the current decision.

### State Management

Every interactive element must have four states defined:
1. **Default** — resting appearance
2. **Hover/Focus** — slight visual change (not relied upon — this is mobile)
3. **Pressed** — `transform: scale(0.98)` + color shift, `motion.fast`
4. **Disabled** — `opacity: 0.5`, `pointer-events: none`, clear visual indication

### Loading States

- Use a centered spinner (36px ring, 3px stroke, `color.brand.primary`)
- Semi-transparent overlay on content area
- Never block the entire screen — allow back navigation during loading

### Empty States

Centered layout with:
- Icon: 48px, stroke `color.text.disabled`, `stroke-width: 1.5`
- Heading: `type.heading.sm`, `color.text.primary`
- Description: `type.body.md`, `color.text.secondary`, max 2 lines
- Optional CTA: Primary button below description, `space.2xl` top margin
- Use cases: no orders, no routes available, no deliveries today, search no results

---

## 7. CSS Variables Reference

Copy this block into any new Fleet Sync screen to ensure token consistency:

```css
:root {
  /* Brand */
  --red: #E60012;
  --red-hover: #D00011;
  --red-light: #FEF0F0;

  /* Status */
  --green: #2EAD4B;
  --green-bg: #F0FFF4;
  --yellow: #D97706;
  --yellow-bg: #FFF8E1;
  --yellow-border: #EED44A;

  /* Neutrals */
  --dark: #1A1A1A;
  --muted: #666666;
  --disabled: #777777;
  --white: #FFFFFF;
  --tile: #F5F5F7;
  --bg: #F2F2F4;
  --border: #E4E5E8;

  /* Spacing */
  --space-xs: 4px;
  --space-sm: 6px;
  --space-md: 8px;
  --space-lg: 12px;
  --space-xl: 14px;
  --space-2xl: 16px;
  --space-3xl: 20px;
  --space-4xl: 24px;

  /* Radii */
  --r: 8px;
  --r-sm: 4px;
  --r-lg: 12px;
  --r-xl: 20px;

  /* Gaps */
  --gap: 12px;

  /* Motion */
  --motion-fast: 150ms;
  --motion-normal: 250ms;
  --motion-slow: 400ms;
  --easing: cubic-bezier(0.4, 0, 0.2, 1);
}
```

---

## 8. File Naming & Organization

```
fleet-sync/
├── design-system.md          ← This file
├── prototype-1.html          ← Home
├── prototype-2.html          ← Choose Orders
├── prototype-3.html          ← Choose Route
├── prototype-4.html          ← Order Verification
├── prototype-5.html          ← Order Completed
└── prototype-6.html          ← Orders List
```

---

## 9. When to Use This Document

Feed this design system to any AI tool (Claude, Cursor, Copilot) when:

- Building new screens for Fleet Sync
- Creating component variants or new states
- Reviewing an existing screen for consistency
- Generating code that needs to match the existing visual language

Paste the **CSS Variables Reference** (Section 7) and the relevant **component spec** into your prompt for best results.
