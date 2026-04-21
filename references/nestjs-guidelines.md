# NestJS Guidelines

Opinionated NestJS conventions for reliable backend services. Use alongside `api-and-interface-design`, `security-and-hardening`, and `test-driven-development`.

## Module and Dependency Design

- [ ] Organize by feature modules (`users`, `billing`, `tasks`) over technical layers only.
- [ ] Keep providers scoped to modules; export only what other modules need.
- [ ] Avoid circular dependencies; refactor shared concerns into dedicated modules.
- [ ] Controllers orchestrate; services contain business logic.

## DTOs and Validation

- [ ] Define DTOs for request payloads and query params.
- [ ] Use `class-validator` + `class-transformer` or schema validation consistently.
- [ ] Enable global validation pipe with whitelist/forbid settings.
- [ ] Treat all external input as untrusted.

## Error Handling and Observability

- [ ] Use `HttpException` (or custom exceptions) with consistent error bodies.
- [ ] Add exception filters for cross-cutting error shaping when needed.
- [ ] Use interceptors for response mapping, timing, and tracing.
- [ ] Log structured fields (request id, user id, route, latency), not only strings.

## Security

- [ ] AuthN/AuthZ enforced with guards (`JwtAuthGuard`, role/permission guards).
- [ ] Secrets loaded via config service; never hardcode credentials.
- [ ] Configure CORS, headers, and rate limiting intentionally.
- [ ] Sanitize and validate data before persistence and rendering.

## Data and Transactions

- [ ] Keep persistence logic in repositories/data services, not controllers.
- [ ] Use transactions for multi-step writes that must succeed together.
- [ ] Avoid N+1 query patterns; batch where possible.
- [ ] Keep migrations reversible and documented.

## Testing

- [ ] Unit test services with mocked boundaries.
- [ ] Integration test modules and providers.
- [ ] E2E test critical API flows with `supertest`.
- [ ] Verify auth/validation/error behavior, not only success paths.

## Tooling and Ops

- [ ] Use environment-based config (`ConfigModule`) with schema validation.
- [ ] Keep OpenAPI docs updated (`@nestjs/swagger`) if used by consumers.
- [ ] Enforce lint/typecheck/test in CI.
- [ ] Include health checks and readiness probes for deployment environments.
