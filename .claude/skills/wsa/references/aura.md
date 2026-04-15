# High-Aura UI/UX: Cinematic Design Principles

This guide defines the standards for "High-Aura" digital experiences. Our goal is to move beyond functional UI into directorial, high-fidelity digital products.

---

## 1. The Atomic Design System (3-Tier Tokens)
To ensure 10/10 consistency, all visual properties must follow a 3-tier tokenization structure.

### Tier 1: Primitive Tokens (Values)
Raw values that define the color palette and constants. Never used directly in components.
```css
:root {
  --color-black-900: #050505;
  --color-indigo-500: #6366f1;
  --font-size-base: 16px;
  --curve-standard: cubic-bezier(0.23, 1, 0.32, 1);
}
```

### Tier 2: Semantic Tokens (Intent)
Maps primitives to an intended use. This allows for instant system-wide changes (e.g., Dark Mode).
```css
:root {
  --sys-bg-canvas: var(--color-black-900);
  --sys-color-primary: var(--color-indigo-500);
  --sys-motion-easing: var(--curve-standard);
  --sys-motion-duration-quick: 150ms;
}
```

### Tier 3: Component Tokens (Scoped)
Maps semantic tokens to specific elements.
```css
.btn-primary {
  background: var(--sys-color-primary);
  transition: all var(--sys-motion-duration-quick) var(--sys-motion-easing);
}
```

---

## 2. Motion GSD: Directorial Principles

### Standardized Easing Curves
- **Standard (Neutral)**: `cubic-bezier(0.4, 0, 0.2, 1)` — for elements moving on-screen within boundaries.
- **Entrance (Deceleration)**: `cubic-bezier(0, 0, 0.2, 1)` — for items appearing from outside the viewport.
- **Exit (Acceleration)**: `cubic-bezier(0.4, 0, 1, 1)` — for items leaving the viewport.

### Staggered Reveal Pattern
Never animate a list at once. Use a staggered reveal to create visual "aura."
```javascript
// GSAP Example
gsap.from(".card", {
  opacity: 0,
  y: 20,
  stagger: 0.05, // 50ms delay between each card
  duration: 0.8,
  ease: "power4.out"
});
```

---

## 3. Visual Depth & Cinematic Surfaces

### Glassmorphism (Premium Depth)
Use layers to simulate hardware-grade craft.
```css
.glass-panel {
  background: rgba(255, 255, 255, 0.03);
  backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
}
```

### Fluid Typography
Agnostic scaling that looks perfect on both mobile (320px) and ultrawide (2k+).
```css
h1 {
  /* clamp(min, preferred, max) */
  font-size: clamp(2.5rem, 5vw + 1rem, 5rem);
  line-height: 1.1;
  letter-spacing: -0.02em;
}
```

---

## 4. Accessibility & Integrity

### Reduced Motion Override
A high-aura system must be inclusive. Always provide a fallback for users with vestibular sensitivities.
```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

### Zero Placeholder Policy
- **Copy**: Use real value propositions. If copy is missing, the AI should research the client's industry to write a "Provisional Hero Lead."
- **Media**: Use curate-only imagery. If an image is required, use `generate_image` with a "Cinematic Tech" or "Clinical Premium" prompt.

---

## 5. Performance Thresholds
- **Animation FPS**: 60fps locked. (Test via Chrome DevTools Rendering tab).
- **LCP (Largest Contentful Paint)**: < 1.2s.
- **CLS (Cumulative Layout Shift)**: 0. If it jumps, it fails.
