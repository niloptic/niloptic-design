# Motion System

Last updated: 2026-03-01

---

## Principle

> Motion reinforces state and data changes only. No decorative animation.

NIL Optic is a data-first platform. Every motion must serve a purpose — confirming an action, revealing content, or communicating a state change. If removing the animation doesn't lose information, the animation shouldn't exist.

---

## Duration Scale

| Token | Value | Usage |
|-------|-------|-------|
| `--motion-instant` | 0ms | Immediate toggles (checkbox, radio) |
| `--motion-fast` | 100ms | Micro-interactions (hover color change) |
| `--motion-standard` | 150ms–220ms | Default transitions (button press, tab switch) |
| `--motion-moderate` | 300ms | Panel slides, card reveals |
| `--motion-slow` | 500ms | Page transitions, modal enters |

---

## Easing

| Name | Curve | Usage |
|------|-------|-------|
| `ease-out` | `cubic-bezier(0, 0, 0.2, 1)` | Element entering view |
| `ease-in` | `cubic-bezier(0.4, 0, 1, 1)` | Element leaving view |
| `ease-in-out` | `cubic-bezier(0.4, 0, 0.2, 1)` | State changes in place |
| `spring` | `cubic-bezier(0.34, 1.56, 0.64, 1)` | Celebratory moments only |

---

## Permitted Motions

| Context | Motion | Duration | Easing |
|---------|--------|----------|--------|
| Button hover | Background color shift | fast | ease-in-out |
| Button press | Scale 0.98 | fast | ease-out |
| Card hover | Subtle border glow | standard | ease-in-out |
| Tab switch | Underline slide | standard | ease-out |
| Modal open | Fade + scale from 0.95 | moderate | ease-out |
| Modal close | Fade + scale to 0.95 | fast | ease-in |
| Toast enter | Slide from right | moderate | ease-out |
| Toast exit | Fade out | fast | ease-in |
| Skeleton load | Pulse shimmer | 1500ms loop | ease-in-out |
| Data update | Number counter | standard | ease-out |
| Navigation | Cross-fade | standard | ease-in-out |

---

## Loading States

Prefer **skeleton loading** over spinners. Skeletons provide spatial context about incoming content.

```
┌─────────────────────────────┐
│  ████████  ──────           │  ← Skeleton header
│                             │
│  ████████████████████       │  ← Skeleton metric (wider)
│                             │
│  ████████████  ─────        │  ← Skeleton body line
│  ██████████████████         │  ← Skeleton body line
└─────────────────────────────┘

Shimmer: left-to-right gradient sweep, 1500ms, ease-in-out, infinite
Color: zinc-800 → zinc-700 → zinc-800 (dark mode)
```

---

## Reduced Motion

When `prefers-reduced-motion: reduce` is active:
- All transitions become instant (0ms)
- Skeleton shimmer becomes static gray
- No scale transforms
- Modal/panel appears without animation
- Respect user system preference — never override
