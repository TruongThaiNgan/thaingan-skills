# UI Foundation Guidelines (Fonts, Spacing, Tokens, shadcn)

Practical UI foundations for app consistency and visual quality. Use alongside `frontend-ui-engineering`.

## 1. Font Selection Logic

Most UI kits default to Inter. Inter is good, but using defaults blindly makes products look interchangeable.

### Recommended Font Strategy

- SaaS / productivity tools:
  - Use Inter or Geist for UI text.
  - Do not introduce a separate heading font; vary weight only.
- Consumer apps:
  - Use Plus Jakarta Sans or DM Sans for a friendlier feel.
- Premium / finance / legal:
  - Use Sora or Neue Haas Grotesk for a more serious tone.
- Landing pages:
  - Display fonts are acceptable for headlines only.
  - Do not use display fonts in product app UI.

### Constraints

- [ ] Prefer 1 font family across the app.
- [ ] Use at most 2 font weights for UI hierarchy.
- [ ] Define font decisions in the design system, not per component.

## 2. Spacing System

If a UI feels "off" despite clean code, spacing inconsistency is a common root cause.

### Spacing Scale

- Base unit: 4px
- Allowed values: 4, 8, 12, 16, 24, 32, 48, 64
- Avoid off-scale values like 13px or 22px

Apply this consistently to:
- margin
- padding
- gap

### Tailwind Notes

- [ ] Use spacing utilities from the defined scale.
- [ ] Avoid ad-hoc overrides that break the spacing rhythm.
- [ ] If spacing is messy with Tailwind, audit custom classes/config first.

## 3. Color Tokens (Semantic, Not Per-Component Hex)

Design systems should use semantic tokens, not raw hex values scattered in components.

### Minimum Token Set

- `background` (page background)
- `surface` (cards, panels, drawers)
- `border`
- `text-primary`
- `text-secondary`
- `brand-primary`
- `brand-secondary` (hover/secondary action)
- `destructive` (error/delete)

### Rules

- [ ] Define tokens centrally (theme/config).
- [ ] Do not hardcode hex in component files.
- [ ] Use semantic names in UI code (`bg-surface`, `text-primary`), not literal colors.

## 4. Using shadcn/ui Correctly

shadcn/ui works well for fast production UI, but only if customization stays token-driven.

### Rules

- [ ] Customize design tokens, not one-off component overrides.
- [ ] Do not mix multiple UI component libraries in the same view.
- [ ] Use `cn()` for class composition instead of manual string concatenation.
- [ ] Extend component variants cleanly; avoid destructive overrides.

## 5. Six High-Impact Visual Decisions

These decisions create visual cohesion quickly:

1. Border radius: choose one default (8px or 12px) and keep it consistent.
2. Shadow: use for layer separation, not decoration.
3. Icons: use one icon set only (for example Lucide or Heroicons).
4. Input height: keep one standard height scale across forms.
5. Hover state: every clickable element must have one.
6. Focus state: replace generic default browser focus with system-consistent focus styles.

## Verification Checklist

- [ ] Font policy documented and applied consistently.
- [ ] Spacing values are on the approved scale.
- [ ] Color usage comes from semantic tokens only.
- [ ] shadcn usage follows token-first customization.
- [ ] Radius, shadows, icons, input sizes, hover, and focus are consistent across screens.
