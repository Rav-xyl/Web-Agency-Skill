# Consistency Reference

## The Rule
Every visual decision must come from a defined system — not from a one-off value.
One magic number anywhere means inconsistency everywhere, eventually.

---

## CSS Design Token System

### Define Once, Use Everywhere

```css
/* tokens.css — import this first in every stylesheet */
:root {
  /* Colours — brand palette */
  --color-primary:     #2563EB;
  --color-primary-hover: #1D4ED8;
  --color-secondary:   #7C3AED;
  --color-accent:      #F59E0B;
  --color-success:     #10B981;
  --color-warning:     #F59E0B;
  --color-error:       #EF4444;

  /* Neutrals */
  --color-bg:          #FFFFFF;
  --color-bg-secondary: #F9FAFB;
  --color-bg-tertiary:  #F3F4F6;
  --color-border:      #E5E7EB;
  --color-border-strong: #D1D5DB;
  --color-text:        #111827;
  --color-text-muted:  #6B7280;
  --color-text-subtle: #9CA3AF;

  /* Typography */
  --font-sans:  'Inter', system-ui, sans-serif;
  --font-serif: 'Merriweather', Georgia, serif;
  --font-mono:  'JetBrains Mono', 'Fira Code', monospace;

  --text-xs:   0.75rem;   /* 12px */
  --text-sm:   0.875rem;  /* 14px */
  --text-base: 1rem;      /* 16px */
  --text-lg:   1.125rem;  /* 18px */
  --text-xl:   1.25rem;   /* 20px */
  --text-2xl:  1.5rem;    /* 24px */
  --text-3xl:  1.875rem;  /* 30px */
  --text-4xl:  2.25rem;   /* 36px */
  --text-5xl:  3rem;      /* 48px */

  --font-normal: 400;
  --font-medium: 500;
  --font-semibold: 600;
  --font-bold: 700;

  --leading-tight:  1.25;
  --leading-snug:   1.375;
  --leading-normal: 1.5;
  --leading-relaxed: 1.625;

  /* Spacing scale — 4px base */
  --space-1:  0.25rem;  /* 4px */
  --space-2:  0.5rem;   /* 8px */
  --space-3:  0.75rem;  /* 12px */
  --space-4:  1rem;     /* 16px */
  --space-5:  1.25rem;  /* 20px */
  --space-6:  1.5rem;   /* 24px */
  --space-8:  2rem;     /* 32px */
  --space-10: 2.5rem;   /* 40px */
  --space-12: 3rem;     /* 48px */
  --space-16: 4rem;     /* 64px */
  --space-20: 5rem;     /* 80px */
  --space-24: 6rem;     /* 96px */

  /* Border radius */
  --radius-sm:   0.25rem;  /* 4px */
  --radius-md:   0.5rem;   /* 8px */
  --radius-lg:   0.75rem;  /* 12px */
  --radius-xl:   1rem;     /* 16px */
  --radius-full: 9999px;

  /* Shadows */
  --shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
  --shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
  --shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
  --shadow-xl: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);

  /* Z-index scale */
  --z-base:    0;
  --z-raised:  10;
  --z-dropdown: 100;
  --z-sticky:  200;
  --z-overlay: 300;
  --z-modal:   400;
  --z-toast:   500;

  /* Transitions */
  --transition-fast:   150ms ease;
  --transition-base:   200ms ease;
  --transition-slow:   300ms ease;

  /* Breakpoints — reference only, use in media queries */
  /* sm: 640px, md: 768px, lg: 1024px, xl: 1280px, 2xl: 1536px */

  /* Container */
  --container-max:    1280px;
  --container-padding: var(--space-4);
}
```

---

## Element Consistency Checklist

Run this on every page before the site is considered done.

### Buttons
All buttons must come from a single button system. No one-off button styles.

```css
/* Button system */
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: var(--space-2);
  padding: var(--space-3) var(--space-6);
  border-radius: var(--radius-md);
  font-size: var(--text-sm);
  font-weight: var(--font-medium);
  line-height: 1;
  cursor: pointer;
  transition: all var(--transition-base);
  border: 1.5px solid transparent;
  text-decoration: none;
}

.btn:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
}

.btn-primary {
  background: var(--color-primary);
  color: white;
}
.btn-primary:hover { background: var(--color-primary-hover); }

.btn-secondary {
  background: transparent;
  border-color: var(--color-border-strong);
  color: var(--color-text);
}
.btn-secondary:hover { background: var(--color-bg-secondary); }

.btn-ghost {
  background: transparent;
  color: var(--color-primary);
}
.btn-ghost:hover { background: var(--color-bg-tertiary); }

.btn:disabled,
.btn[aria-disabled="true"] {
  opacity: 0.5;
  cursor: not-allowed;
  pointer-events: none;
}

/* Sizes */
.btn-sm { padding: var(--space-2) var(--space-4); font-size: var(--text-xs); }
.btn-lg { padding: var(--space-4) var(--space-8); font-size: var(--text-base); }
```

**Audit:** Grep for `<button` and `<a` styled as buttons across all files.
Check every instance uses `.btn` + modifier. No inline styles on buttons.

### Typography
```css
/* Typography system */
h1 { font-size: var(--text-4xl); font-weight: var(--font-bold); line-height: var(--leading-tight); }
h2 { font-size: var(--text-3xl); font-weight: var(--font-bold); line-height: var(--leading-tight); }
h3 { font-size: var(--text-2xl); font-weight: var(--font-semibold); line-height: var(--leading-snug); }
h4 { font-size: var(--text-xl);  font-weight: var(--font-semibold); line-height: var(--leading-snug); }
h5 { font-size: var(--text-lg);  font-weight: var(--font-medium);   line-height: var(--leading-normal); }
h6 { font-size: var(--text-base);font-weight: var(--font-medium);   line-height: var(--leading-normal); }
p  { font-size: var(--text-base); line-height: var(--leading-relaxed); color: var(--color-text); }
```

**Audit:** Check every heading across all pages uses system sizes. No `font-size: 28px` etc.

### Forms
```css
/* Form system */
.form-label {
  display: block;
  font-size: var(--text-sm);
  font-weight: var(--font-medium);
  color: var(--color-text);
  margin-bottom: var(--space-2);
}

.form-input {
  width: 100%;
  padding: var(--space-3) var(--space-4);
  border: 1.5px solid var(--color-border);
  border-radius: var(--radius-md);
  font-size: var(--text-base);
  color: var(--color-text);
  background: var(--color-bg);
  transition: border-color var(--transition-base);
}
.form-input:focus {
  outline: none;
  border-color: var(--color-primary);
  box-shadow: 0 0 0 3px rgb(37 99 235 / 0.1);
}
.form-input:disabled { background: var(--color-bg-tertiary); cursor: not-allowed; }
.form-input.error { border-color: var(--color-error); }

.form-error {
  font-size: var(--text-sm);
  color: var(--color-error);
  margin-top: var(--space-1);
}

.form-hint {
  font-size: var(--text-sm);
  color: var(--color-text-muted);
  margin-top: var(--space-1);
}
```

### Cards
```css
.card {
  background: var(--color-bg);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: var(--space-6);
  box-shadow: var(--shadow-sm);
}
.card-hover {
  transition: box-shadow var(--transition-base), transform var(--transition-base);
}
.card-hover:hover {
  box-shadow: var(--shadow-md);
  transform: translateY(-2px);
}
```

### Links
```css
a {
  color: var(--color-primary);
  text-decoration: underline;
  text-underline-offset: 3px;
  transition: color var(--transition-fast);
}
a:hover { color: var(--color-primary-hover); }
a:visited { color: var(--color-secondary); }
a:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
  border-radius: var(--radius-sm);
}
```

---

## Spacing Consistency Rules

- **Between sections**: `var(--space-20)` to `var(--space-24)` (80–96px)
- **Inside containers / cards**: `var(--space-6)` to `var(--space-8)` (24–32px)
- **Between related elements** (label→input, icon→text): `var(--space-2)` (8px)
- **Between list items**: `var(--space-3)` to `var(--space-4)` (12–16px)
- **Never use**: arbitrary px values like `margin: 17px` or `padding: 23px`

---

## Responsive Breakpoints

```css
/* Use these breakpoints consistently across ALL files */
@media (max-width: 640px)  { /* mobile */ }
@media (max-width: 768px)  { /* tablet */ }
@media (max-width: 1024px) { /* small desktop */ }
@media (max-width: 1280px) { /* large desktop */ }

/* Mobile-first approach (preferred): */
/* base styles = mobile */
@media (min-width: 768px)  { /* tablet and up */ }
@media (min-width: 1024px) { /* desktop and up */ }
```

**Never mix** `max-width` and `min-width` breakpoints on the same project without
documenting which approach is in use. Pick one and enforce it everywhere.

---

## CSS Audit Commands

```bash
# Find hardcoded colour values (should be using variables)
grep -rn "#[0-9a-fA-F]\{3,6\}" --include="*.css" --include="*.scss" .

# Find inline styles in HTML/JSX (should not exist)
grep -rn 'style="' --include="*.html" --include="*.jsx" --include="*.tsx" .

# Find magic number spacing (px values not from scale)
grep -rn "[0-9]\+px" --include="*.css" . | grep -v "var(" | grep -v "border" | grep -v "0px"

# Find duplicate CSS rules (install: https://github.com/nickmanning/css-duplicate-properties)
# Or paste CSS into: https://cssstats.com
```

---

## Consistency Audit — Final Pass

Go page by page. For each page check:

| Element | Consistent? | Notes |
|---------|------------|-------|
| H1 style | | |
| H2 style | | |
| Body text | | |
| Primary button | | |
| Secondary button | | |
| Form inputs | | |
| Form labels | | |
| Form errors | | |
| Card style | | |
| Navigation | | |
| Footer | | |
| Link colour | | |
| Link hover | | |
| Icon library | | |
| Image aspect ratio | | |
| Section padding | | |
| Container max-width | | |
| Border radius | | |
| Shadow style | | |

Any row that says "No" = fix before launch.
