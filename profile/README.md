<div align="center">

<img width="2560" height="640" alt="Afora Framework Banner" src="https://github.com/user-attachments/assets/c7df04bf-316e-461c-aa60-34f6bb0cd3b6" />

<br/>

**English** &nbsp;•&nbsp; [Português (Brasil)](https://github.com/afora-framework/.github/blob/main/profile/README.pt-br.md)

<br/>

### Beyond conventional limits. Engineered for modern, resilient domain-driven software.

[![GitHub Org](https://img.shields.io/badge/organization-afora--framework-242938?style=for-the-badge&logo=github&logoColor=white)](https://github.com/afora-framework)
[![License](https://img.shields.io/badge/license-MIT-8FB59A?style=for-the-badge)](https://github.com/afora-framework/core)
[![Status](https://img.shields.io/badge/status-active%20development-E08A63?style=for-the-badge)](https://github.com/afora-framework/core)

</div>

---

### 🌿 About Afora Framework

**Afora** is a modern TypeScript framework built for robust, expressive **Domain Modeling and Domain-Driven Design (DDD)** on top of [TypeBox](https://github.com/sinclairzx81/typebox). Designed from the ground up to integrate with any [Standard Schema V1](https://standardschema.dev) consumer (such as Hono, tRPC, and TanStack Form), Afora brings rigor and ergonomics to application boundaries and domain logic.

Rather than being another generic data validator, Afora structures your core business entities with strict invariants, masked sensitive data, typed change workflows, layered exceptions, and first-class AI agent tooling.

---

### ✨ Core Pillars

- 🧩 **Domain Modeling & Invariants**: Define properties (`Email`, `Slug`, `Password`), blueprints, and records that validate and normalize every value, rejecting undeclared keys at any depth.
- 🔒 **Sensitive Data Protection**: Fields flagged as `sensitive` (such as `Password`) are automatically masked in `toJSON()` at any depth, ensuring zero accidental leaks in logs or APIs.
- 🏛️ **Entities, Repositories & Use Cases**: `entityOf` manages identity, audit timestamps, and domain events; `repositoryOf` auto-generates typed query methods (such as `findBy<Key>`); use cases encapsulate orchestration and dependency injection.
- 🛡️ **Layer-Aware Exceptions**: Detailed exceptions that know their architectural layer (`Property`, `Record`, `Repository`, `UseCase`) and accumulate execution traces as they traverse your layers.
- ⚡ **Standard Schema & Multi-Runtime**: Native compliance with Standard Schema V1 on every field. Engineered for [Bun](https://bun.sh) and Node.js (>= 22), loading cleanly in browsers and Workers with zero crypto overhead at import.
- 🤖 **AI-Ready & Declarative**: Native MCP server (`@afora/mcp`) and code generator (`@afora/codegen`) to let developers and AI agents specify and build domain systems together.

---

### 📦 Ecosystem & Repositories

| Package / Repository | Description | Status |
| :--- | :--- | :--- |
| [**`core`** (`@afora/core`)](https://github.com/afora-framework/core) | Core domain engine: Properties, Blueprints, Records, Entities, Repositories, Use Cases, and interactive local Playground | 🚧 Active Development |
| [**`@afora/codegen`**](https://github.com/afora-framework/core/tree/main/packages/codegen) | Declarative domain specifications (`afora.json`) with deterministic, bi-directional TypeScript generation | 🚧 Active Development |
| [**`@afora/mcp`**](https://github.com/afora-framework/core/tree/main/packages/mcp) | Model Context Protocol (MCP) server enabling AI agents to design, validate, and scaffold Afora domains | 🚧 Active Development |

---

### 🚀 Interactive Playground

`@afora/core` includes an integrated local playground powered by Monaco Editor and TypeScript language services to experiment with domain models, test invariants, and inspect masked outputs in real time:

```bash
bun add @afora/core
bun run playground
```

---

### 🤝 Contributing & Community

We welcome developers, architects, and open-source enthusiasts who want to shape the future of domain-driven engineering!

- 💡 **Discussions & Feedback**: Share ideas, propose RFCs, or ask questions in our repository discussions and issues.
- 🛠️ **Pull Requests**: Check out open issues on our [core repository](https://github.com/afora-framework/core).
- 🐞 **Issue Reporting**: Found a bug or have a suggestion? Open an issue in the respective repository.

---

<div align="center">
  <sub>Crafted with passion by the <strong>Afora Framework</strong> community.</sub>
</div>
