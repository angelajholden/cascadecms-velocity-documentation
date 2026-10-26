# Cascade CMS & Apache Velocity Documentation

Practical reference guides for building, maintaining, and publishing websites with **Cascade CMS** and **Apache Velocity**.

These independently written guides explain Cascade's content architecture, reusable assets, Velocity Formats, integrations, and publishing workflows. They are intended for developers learning Cascade and for those maintaining existing implementations.

> **Scope:** General developer reference—not documentation for any one client or institution. Features, menu labels, and permissions may vary by Cascade CMS version.

## Documentation

1. [Getting Started](01-getting-started/README.md) — concepts, architecture, and site setup; begin with [How a Cascade Page Is Built](01-getting-started/cascade-architecture.md).
2. [Cascade Development](02-cascade-development/README.md) — content types, data definitions, shared fields, templates, blocks, formats, and asset factories.
3. [Apache Velocity](03-apache-velocity/README.md) — directives, macros, structured data, and Cascade-specific Velocity tools.
4. [APIs & Integrations](04-apis-and-integrations/README.md) — JSON publishing, feeds, and API-driven frontend features.
5. [Publishing & Deployment](05-publishing-and-deployment/README.md) — outputs, destinations, transports, release checklists, and testing.
6. [Troubleshooting](06-troubleshooting/README.md) — diagnosing rendering, configuration, and publishing problems.

## Guide format

Each completed guide will include:

- **Overview:** what the feature does and why it matters.
- **Prerequisites:** required permissions, assets, and assumptions.
- **Steps:** procedures written for a generic Cascade site.
- **Examples:** original Velocity, HTML, or JSON as appropriate.
- **Verification:** how to test in an authorized development environment.
- **Troubleshooting:** common mistakes and checks.
- **References:** links to the relevant official documentation.

## Principles

- Examples use fictional sites, fields, URLs, and data—never client-specific assets.
- Distinguish standard **Apache Velocity** syntax from **Cascade CMS** global variables and tools.
- Attribute third-party references and write original explanations and code examples.
- Verify version-specific behavior against official docs and a test installation before relying on it in production.
- Keep client-specific implementation guides in separate, private documentation.

## Official references

- [Cascade CMS Knowledge Base](https://www.hannonhill.com/cascadecms/latest/articles/index.html)
- [Templates, Configuration Sets, and Outputs](https://www.hannonhill.com/cascadecms/latest/articles/design-in-cascade/templates-formats-outputs.html)
- [Developing in Cascade](https://www.hannonhill.com/cascadecms/latest/articles/developing-in-cascade/index.html)
- [Velocity Tools](https://www.hannonhill.com/cascadecms/latest/articles/developing-in-cascade/script-formats/velocity-tools.html)
- [Apache Velocity](https://velocity.apache.org/)

## About

Created by [Angela J. Holden](https://github.com/angelajholden), a software engineer focused on frontend development, CMS implementation, accessibility, deployment, and technical documentation.

Independent community documentation; not affiliated with or endorsed by Hannon Hill or the Apache Software Foundation.
