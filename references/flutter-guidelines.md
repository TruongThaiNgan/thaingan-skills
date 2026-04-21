# Flutter Guidelines

Production-focused Flutter practices for maintainability, performance, and UX quality. Use alongside `frontend-ui-engineering` and `code-review-and-quality`.

## Architecture

- [ ] Separate presentation, state, and data concerns.
- [ ] Prefer feature-based folders over layer-only dumps.
- [ ] Keep widgets small and composable.
- [ ] Avoid business logic in widget build methods.

## Performance and Rebuilds

- [ ] Use `const` constructors/widgets when possible.
- [ ] Keep `setState` scope narrow.
- [ ] Avoid expensive work inside `build()`.
- [ ] Use lazy lists (`ListView.builder`, `SliverList`) for large collections.
- [ ] Add keys for reorderable/dynamic list items.

## State Management

- [ ] Pick one primary state pattern per app area (Provider/Riverpod/Bloc/etc.).
- [ ] Avoid mixing many state paradigms without clear boundaries.
- [ ] Keep side effects in controllers/notifiers, not UI widgets.
- [ ] Model loading/error/empty/success explicitly.

## Styling, Theming, and i18n

- [ ] Centralize theme setup (`ThemeData`, color/text tokens).
- [ ] Avoid hardcoded styles and magic numbers.
- [ ] Route user-facing strings through localization (`intl`/l10n generation).
- [ ] Keep typography/spacing consistent with design tokens.

## Navigation and Routing

- [ ] Define routes centrally (Router/go_router route tree).
- [ ] Protect auth-only routes with guards/redirect logic.
- [ ] Pass typed route arguments where possible.
- [ ] Handle deep links intentionally.

## Null Safety and Types

- [ ] Prefer non-nullable fields by default.
- [ ] Use nullable types only for valid absence states.
- [ ] Use `final` by default; use `late` sparingly and intentionally.
- [ ] Model state with enums/sealed unions when states are finite.

## Testing

- [ ] Unit tests for domain logic.
- [ ] Widget tests for key interactions and render states.
- [ ] Integration tests for critical user flows.
- [ ] Golden tests only where visual regression value is clear.

## Tooling

- [ ] `flutter analyze` clean or justified.
- [ ] `dart format` applied.
- [ ] Lints configured (`flutter_lints` + project custom rules).
- [ ] CI enforces analyze/test on PRs.
