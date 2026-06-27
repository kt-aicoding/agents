# MCP HTTP Proxy Maintenance Guide

## Project State

- Repository: `kevinten-ai/mcp-http-proxy`
- Category: Spring Boot HTTP-to-MCP bridge
- Runtime: Java 25, Spring Boot 3.5, official MCP Java SDK
- Public deployment: none recorded in the current workspace inventory.

## Before Editing

- Keep SSRF protections strict. Changes to domain allowlists, URL parsing, redirects, or internal IP checks require tests.
- Do not commit `target/`, runtime logs, local `.env` files, or real upstream MCP credentials.
- Treat `serverUrl`, headers, and tool parameters as untrusted input.

## Useful Commands

- Compile: `mvn clean compile`
- Test: `mvn test`
- Package: `mvn clean package`
- Run locally: `mvn spring-boot:run`
- Docker compose smoke check: `docker compose config`

## Environment

- Copy `.env.example` for local shell configuration if needed.
- The primary service configuration is still `application.yml` / Spring environment variables.

## Deployment Notes

- See `DEPLOYMENT.md` for Docker, Compose, and runtime validation steps.
- Default API root is `http://localhost:8080/api/v1`.
