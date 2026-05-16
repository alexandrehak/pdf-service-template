# pdf-service Agent Instructions

A JavaScript microservice that processes queue messages to generate PDFs, targeting **< 100ms per message** with minimal dependencies.

## Tech Stack

- **API**: [Hono](https://hono.dev/) — follow [RESTful API best practices](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design)
- **PDF generation**: [libpdf](https://github.com/libpdf-js/core)
- **Observability**: Grafana (metrics, dashboards, alerting)
- **Architecture**: [Microservice](https://microservices.io/patterns/microservices.html) — queue-based worker

## API Behavior

- The PDF endpoint must return a **streamed response** (do not buffer the full PDF before sending)
- A stats page must display the count of available PDF templates **when a DB connection is configured** (gracefully degrade when no DB)

## Conventions

### Commits
Use [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) — enforced by [commit-check](https://github.com/commit-check/commit-check):
```
<type>(scope): <description>

Types: feat | fix | perf | refactor | test | docs | chore | ci
```

### Branches
Use [Conventional Branch](https://conventional-branch.github.io/) naming:
```
<type>/<short-description>   e.g. feat/add-invoice-template
```

## Performance Rules

- Keep queue message processing under **100 ms**
- Minimize dependencies — justify every new package
- Prefer native Node.js APIs over third-party libs when equivalent

## Project Structure (planned)

```
src/
  api/        # Hono route handlers
  queue/      # Queue worker logic
  pdf/        # libpdf wrappers and templates
  observability/  # Grafana metrics instrumentation
```

## Deployment

The service must be deployable via:
1. **Docker** — provide a Dockerfile
2. **Direct (ZIP)** — document node version and startup command; the service should be packageable as a ZIP for direct deployment

## What to Avoid

- Do not add dependencies without clear justification
- Do not bypass the queue abstraction for direct PDF generation calls
- Do not hardcode cloud-provider-specific APIs — keep the service portable
