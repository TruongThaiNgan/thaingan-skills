# Dart and Flutter Review Checklist

Use this checklist as an add-on to `code-review-and-quality` for Flutter and Dart changes.

## Correctness

- [ ] Behavior matches the feature spec or bug report.
- [ ] Widget tests/integration tests cover success, empty, error, and retry states.
- [ ] Async error handling is explicit (`try/catch`, failure UI, fallback behavior).
- [ ] List mutations/reordering use stable keys where needed.

## Readability

- [ ] Names follow conventions (`snake_case` file, `PascalCase` type, `camelCase` member).
- [ ] Long callbacks are extracted to named methods.
- [ ] Trailing commas are used in multiline collections/constructor calls.
- [ ] Widget trees are split when nesting becomes hard to scan.

## Architecture

- [ ] UI, state, and data responsibilities are clearly separated.
- [ ] State management choice is consistent with existing project pattern.
- [ ] Routes and themes are defined in centralized modules.
- [ ] No duplicate utilities/extensions introduced without clear need.

## Security

- [ ] No secrets or tokens hardcoded in source, logs, or test snapshots.
- [ ] External/API data is treated as untrusted and validated at boundaries.
- [ ] Sensitive data is not displayed or logged without redaction.

## Performance

- [ ] `const` is used where valid to reduce unnecessary rebuilds.
- [ ] `setState` calls are scoped narrowly.
- [ ] Expensive work is not done in `build()`.
- [ ] Large lists use lazy builders and pagination where appropriate.

## Null Safety and Types

- [ ] Nullable types are used only when absence is a valid state.
- [ ] `late` is justified and initialization order is safe.
- [ ] `final` is used by default where reassignment is unnecessary.

## Imports, Lints, and Tooling

- [ ] Import style is consistent with repo convention (`package:` for `lib/` in most Flutter apps).
- [ ] `flutter analyze` is clean or deviations are documented.
- [ ] Lints are enforced in CI (`flutter_lints` and project custom rules).

## Modern Dart

- [ ] Records/pattern matching/switch expressions are used when they simplify logic.
- [ ] New language features improve clarity, not cleverness.
