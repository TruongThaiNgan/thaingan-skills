# TypeScript Guidelines

Type safety and maintainability checklist for TypeScript codebases. Use alongside `api-and-interface-design`, `test-driven-development`, and `code-review-and-quality`.

## Type Safety Baseline

- [ ] `strict` mode enabled.
- [ ] Avoid `any`; use `unknown` at boundaries and narrow explicitly.
- [ ] Prefer explicit return types on exported/public functions.
- [ ] Enable `noUncheckedIndexedAccess` and `exactOptionalPropertyTypes` when practical.

## API and Domain Modeling

- [ ] Use discriminated unions for variant states.
- [ ] Model domain invariants with precise types, not comments.
- [ ] Separate input DTO types from internal domain models.
- [ ] Prefer additive schema evolution over breaking type changes.

## Code Style and Structure

- [ ] Prefer `const` and immutable patterns where practical.
- [ ] Keep functions focused and side effects explicit.
- [ ] Avoid over-generic abstractions before proven reuse.
- [ ] Use utility types (`Pick`, `Omit`, `Partial`) intentionally, not to hide poor modeling.

## Runtime Validation

- [ ] Validate untrusted data at boundaries (HTTP, env, queue, DB JSON fields).
- [ ] Keep parsed/validated types separate from raw payloads.
- [ ] Never assume third-party response shapes without checks.

## Error Handling

- [ ] Use typed error categories/codes for predictable handling.
- [ ] Preserve original causes where possible.
- [ ] Avoid swallowing errors in broad `catch` blocks.
- [ ] Ensure async workflows return rejected promises on failure paths.

## Testing

- [ ] Tests assert behavior and contracts, not implementation details.
- [ ] Type-level edge cases are covered in runtime tests where relevant.
- [ ] Add regression tests for every bug fix.
- [ ] Mock only boundaries (network, DB, filesystem, clock).

## Tooling

- [ ] `tsc --noEmit` passes in CI.
- [ ] ESLint TypeScript rules enabled and clean.
- [ ] Dead code/unused exports are detected (`noUnusedLocals`, lint plugins).
- [ ] `tsconfig` differences between app/test/build are intentional and documented.
