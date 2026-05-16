# pdf-service-template

A modern, actively maintained template for creating a PDF service using JavaScript. Designed to deliver an optimal queue worker experience with best-in-class performance and minimal overhead.

## Features

- It should process a queue message under 100 ms
- It should be as lightweight as possible
- It should use the least depedencies possible
- It should be deployable on any major cloud provider services

## Deployment

## Observability

Grafana tools should be used
- It uses [OpenTelemetry](https://github.com/honojs/middleware/tree/main/packages/otel)
- Consider using [Sentry](https://github.com/honojs/middleware/tree/main/packages/sentry)

### Monitoring

## Git workflow

This project follows [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow).

## Notes

- This is a service design for [Microservice Architecture](https://microservices.io/patterns/microservices.html)
- It uses [hono](https://hono.dev/) for API stuff
  - It follows [Best practices for RESTful web API design](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design)
  - Add an example for invoices handling
- It uses [libpdf](https://github.com/libpdf-js/core) for PDF stuff
- Add testing automation
- Add benchmarking automation
- Add a guide for local development (contributing.md)
- Add a guide for deployment
  - It should be possible to deploy via docker
  - It should be possible to be deployed directly as a ZIP
- Add system design guide and recommendations
- Add an example of design
- It should expose a client-callable API that returns a streamed response
- It should expose a page that displays the number of available PDF templates when a database connection is configured
- run `/init` in copilot to update chat customization files for AI coding agents

## Todo

- ai-agent: add instruction to use [conventional commit](https://www.conventionalcommits.org/en/v1.0.0/) and [conventional branch](https://conventional-branch.github.io/)
- ai-agent: add skills.md
- [ ] cicd: automate deployment
- [ ] use [commit-check](https://github.com/commit-check/commit-check) to enforce git conventions

### vscode

- [ ] configure vscode workspace settings

## APIs

### Documentation

- use Swagger UI or Scalar based on OpenAPI
