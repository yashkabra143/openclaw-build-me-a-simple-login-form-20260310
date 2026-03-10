# Design Specification

**Project:** build me a simple login form
**Date:** 2026-03-10
**Agent:** design-agent

---

# Comprehensive Design Specification
## User Authentication Login Form — Design System & Component Spec

**Version:** 1.0 | **Status:** Ready for Development | **Based on PRD:** v1.0

---

## Table of Contents

1. [Design System Foundation](#1-design-system-foundation)
2. [Component Inventory](#2-component-inventory)
3. [Screen Layouts](#3-screen-layouts)
4. [Navigation Structure](#4-navigation-structure)
5. [Interaction Patterns](#5-interaction-patterns)
6. [Responsive Breakpoints](#6-responsive-breakpoints)
7. [Accessibility Requirements](#7-accessibility-requirements)
8. [Tech Stack Implementation Guide](#8-tech-stack-implementation-guide)

---

## 1. Design System Foundation

### 1.1 Design Philosophy

The login form must communicate **trust, clarity, and speed**. Every visual decision serves one of three principles:

- **Reduce cognitive load** — The user should never have to think about what to do next
- **Signal security without friction** — Visual cues build confidence without adding steps
- **Accessible by default** — Not an afterthought; every token is chosen with contrast and clarity in mind

---

### 1.2 Color Palette

All colors are defined as CSS custom properties. Tailwind config extensions are provided in Section 8.

#### Brand / Primary Colors

| Token | Hex | Tailwind Class | Usage | Contrast on White |
|---|---|---|---|---|
| `--color-primary-500` | `#2563EB` | `primary-500` | Primary CTA, links, focus rings | 4.63:1 ✅ AA |
| `--color-primary-600` | `#1D4ED8` | `primary-600` | CTA hover state | 5.74:1 ✅ AA |
| `--color-primary-700` | `#1E40AF` | `primary-700` | CTA active/pressed state | 7.18:1 ✅ AAA |
| `--color-primary-50` | `#EFF6FF` | `primary-50` | Focus ring fill, subtle highlights | N/A — background use only |
| `--color-primary-100` | `#DBEAFE` | `primary-100` | Input focus background tint | N/A — background use only |

#### Neutral / Surface Colors

| Token | Hex | Tailwind Class | Usage |
|---|---|---|---|
| `--color-neutral-0` | `#FFFFFF` | `white` | Form card background, input backgrounds |
| `--color-neutral-50` | `#F8FAFC` | `neutral-50` | Page background |
| `--color-neutral-100` | `#F1F5F9` | `neutral-100` | Disabled input background |
| `--color-neutral-200` | `#E2E8F0` | `neutral-200` | Default input border, dividers |
| `--color-neutral-300` | `#CBD5E1` | `neutral-300` | Placeholder text on white (fails AA — use neutral-500 instead) |
| `--color-neutral-500` | `#64748B` | `neutral-500` | Placeholder text, helper text, secondary labels |
| `--color-neutral-700` | `#334155` | `neutral-700` | Secondary body text |
| `--color-neutral-900` | `#0F172A` | `neutral-900` | Primary body text, labels |

> ⚠️ **Critical:** Never use `neutral-300` or lighter for text. Minimum for body text is `neutral-500` (#64748B) which achieves 4.60:1 on white — just meeting AA for large text. For small/body text, use `neutral-700` (8.97:1) or `neutral-900` (17.1:1).

#### Semantic Colors

| Token | Hex | Tailwind Class | Usage | Contrast on White |
|---|---|---|---|---|
| `--color-error-500` | `#DC2626` | `error-500` | Error text, error icon | 5.74:1 ✅ AA |
| `--color-error-600` | `#B91C1C` | `error-600` | Error text on light backgrounds | 7.43:1 ✅ AAA |
| `--color-error-50` | `#FEF2F2` | `error-50` | Error state input background tint | N/A — background |
| `--color-error-200` | `#FECACA` | `error-200` | Error state input border | N/A — border use only |
| `--color-success-500` | `#16A34A` | `success-500` | Success states | 4.54:1 ✅ AA |
| `--color-success-50` | `#F0FDF4` | `success-50` | Success background tint | N/A — background |
| `--color-warning-500` | `#D97706` | `warning-500` | Warning states (locked account banner) | 3.15:1 ⚠️ Use only for icons with text label |
| `--color-warning-700` | `#92400E` | `warning-700` | Warning text — use this, not warning-500 | 7.53:1 ✅ AAA |
| `--color-warning-50` | `#FFFBEB` | `warning-50` | Warning background | N/A — background |

#### Dark Mode Tokens

| Token | Light Value | Dark Value | Usage |
|---|---|---|---|
| `--color-surface` | `#FFFFFF` | `#1E293B` | Card/form background |
| `--color-surface-subtle` | `#F8FAFC` | `#0F172A` | Page background |
| `--color-border-default` | `#E2E8F0` | `#334155` | Input default border |
| `--color-border-focus` | `#2563EB` | `#60A5FA` | Input focus border |
| `--color-text-primary` | `#0F172A` | `#F1F5F9` | Labels, body text |
| `--color-text-secondary` | `#64748B` | `#94A3B8` | Helper text, placeholders |
| `--color-text-link` | `#2563EB` | `#60A5FA` | Links |

---

### 1.3 Typography Scale

**Font Family:**
```
--font-sans: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
```

Inter is specified for its exceptional legibility at small sizes, extensive weight range, and optimized tabular numerals for form contexts. It is available via Google Fonts with `display=swap` for performance.

**Loading Strategy:**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
```

#### Type Scale

| Token | Size | Line Height | Weight | Letter Spacing | Usage |
|---|---|---|---|---|---|
| `text-display` | 30px / 1.875rem | 1.2 (36px) | 700 | -0.02em | Page title "Welcome back" — desktop only |
| `text-heading-lg` | 24px / 1.5rem | 1.25 (30px) | 700 | -0.01em | Page title "Welcome back" — mobile |
| `text-heading-md` | 20px / 1.25rem | 1.3 (26px) | 600 | -0.01em | Section subheadings |
| `text-body-lg` | 16px / 1rem | 1.5 (24px) | 400 | 0 | Form input text, body copy |
| `text-body-md` | 14px / 0.875rem | 1.5 (21px) | 400 | 0 | Helper text, secondary labels |
| `text-body-sm` | 13px / 0.8125rem | 1.5 (19.5px) | 400 | 0 | Inline error messages |
| `text-label` | 14px / 0.875rem | 1.4 (19.6px) | 500 | 0 | Input labels |
| `text-label-sm` | 13px / 0.8125rem | 1.4 (18.2px) | 500 | 0 | Checkbox label, small caps label |
| `text-button` | 15px / 0.9375rem | 1 | 600 | 0.01em | Button text |
| `text-link` | 14px / 0.875rem | 1.5 | 500 | 0 | Inline links |

> **Minimum text size rule:** No interactive text smaller than 13px. No static informational text smaller than 12px. Both rules exist for WCAG 1.4.4 compliance.

---

### 1.4 Spacing System

Based on a **4px base unit**. All spacing values are multiples of 4.

| Token | Value | Tailwind | Usage |
|---|---|---|---|
| `space-1` | 4px | `p-1`, `gap-1` | Icon internal padding, tight nudges |
| `space-2` | 8px | `p-2`, `gap-2` | Label-to-input gap, icon-to-text |
| `space-3` | 12px | `p-3`, `gap-3` | Input internal vertical padding |
| `space-4` | 16px | `p-4`, `gap-4` | Input internal horizontal padding, card padding (mobile) |
| `space-5` | 20px | `p-5`, `gap-5` | Between form fields (stacked) |
| `space-6` | 24px | `p-6`, `gap-6` | Between major sections within form |
| `space-8` | 32px | `p-8`, `gap-8` | Card padding (desktop), between heading and form |
| `space-10` | 40px | `p-10`, `gap-10` | Card padding top/bottom (desktop) |
| `space-12` | 48px | `p-12`, `gap-12` | Max-width container side padding |
| `space-16` | 64px | `p-16`, `gap-16` | Vertical centering margin |

#### Spacing Application Rules

- **Label to Input:** `space-2` (8px) — tight enough to show association, enough to be distinct
- **Input to Error Message:** `space-2` (8px)
- **Between Fields:** `space-5` (20px)
- **Between Checkbox Row and Submit Button:** `space-6` (24px)
- **Form Card Padding (desktop):** `space-8` horizontal, `space-10` vertical
- **Form Card Padding (mobile):** `space-6` horizontal, `space-8` vertical

---

### 1.5 Border Radius System

| Token | Value | Tailwind | Usage |
|---|---|---|---|
| `radius-sm` | 4px | `rounded-sm` | Checkboxes, small badges |
| `radius-md` | 6px | `rounded-md` | Buttons, inputs |
| `radius-lg` | 8px | `rounded-lg` | Alert/banner components |
| `radius-xl` | 12px | `rounded-xl` | Form card (mobile: 0 — full width) |
| `radius-full` | 9999px | `rounded-full` | Focus ring on icon buttons, pill badges |

---

### 1.6 Shadow / Elevation System

| Token | Value | Tailwind | Usage |
|---|---|---|---|
| `shadow-sm` | `0 1px 2