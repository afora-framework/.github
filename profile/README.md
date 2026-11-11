<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/afora-framework/core/main/.github/assets/afora-banner-dark.png">
  <img alt="afora — Simple to write. Built to hold." src="https://raw.githubusercontent.com/afora-framework/core/main/.github/assets/afora-banner-light.png" width="100%">
</picture>

**English** &nbsp;·&nbsp; [Português (Brasil)](https://github.com/afora-framework/.github/blob/main/profile/README.pt-br.md)

### Simple to write. Built to hold.

[![npm](https://img.shields.io/npm/v/@afora/core?color=E4572E&label=%40afora%2Fcore)](https://www.npmjs.com/package/@afora/core)
[![MIT license](https://img.shields.io/badge/license-MIT-4E7C5B)](https://github.com/afora-framework/core/blob/main/LICENSE)
[![Standard Schema V1](https://img.shields.io/badge/Standard%20Schema-V1-21504F)](https://standardschema.dev)
[![Before 1.0](https://img.shields.io/badge/status-before%201.0-F0B44C)](https://github.com/afora-framework/core/blob/main/VERSIONING.md)

</div>

**afora is a domain-first framework for TypeScript backends.** You declare what your entities, use cases and API are, and the runtime keeps the guarantees that are easy to forget. Whoever writes the code, you or your agent, it holds.

Model the domain; the runtime keeps the invariants. Built on [TypeBox](https://github.com/sinclairzx81/typebox), with [Standard Schema](https://standardschema.dev) on every field, on Bun and Node.

### Why afora

An HTTP backend written by an agent, or in a hurry, tends to break the same few guarantees. In afora each one is part of the runtime:

| What usually breaks                         | What afora does                                                        |
| ------------------------------------------- | ---------------------------------------------------------------------- |
| A password hash ends up in a response       | A `sensitive` property is masked by `toJSON()` at any depth.           |
| Extra fields in a request body are accepted | Undeclared keys are rejected at any depth; the API answers 400.        |
| A business error is returned as a 500       | Errors know their layer and become problem+json with the right status. |
| A duplicate email is written twice          | `unique` keys are enforced by the repository; a violation is a 409.    |

### For you and your agent

**Developer experience.** Four declarations to a CRUD API. Types that follow the model: `findByEmail` exists because `email` is unique. Any server (Hono, Fastify, Express, Elysia) and any store (in memory, Drizzle, DynamoDB).

**Agent experience.** The whole application is data: an `afora.json` declares the entities, the use cases as steps and the HTTP API. An MCP server lets an agent write it, codegen turns it into TypeScript you review, and the runtime holds what the agent forgets.

### A quick look

```ts
export class User extends entityOf(
	blueprintOf((ctx) => ({
		name: ctx.text,
		email: ctx.email, // trimmed and lowercased
		password: ctx.password, // only an argon2 hash is accepted; always masked
	})),
	{ unique: ["email"] },
) {}
```

```
POST /api/users  { "name": "Ana", "email": "  Ana@Example.COM ", "plainPassword": "Str0ng!Pass" }
-> 201 { "user": { "id": "...", "name": "Ana", "email": "ana@example.com", "password": "********", ... } }

the same email again
-> 409 application/problem+json  { "title": "UserAlreadyExists", "layer": "use-case", ... }
```

The whole example, and the same app as an `afora.json`, is the [quick start](https://github.com/afora-framework/core#quick-start).

### Packages

| Package                                                                                  | What it does                                                      |
| ---------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| [`@afora/core`](https://github.com/afora-framework/core)                                 | The framework: from properties to outputs.                        |
| [`@afora/codegen`](https://github.com/afora-framework/core/tree/main/packages/codegen)   | `afora.json` to TypeScript, and an application back to its spec.  |
| [`@afora/mcp`](https://github.com/afora-framework/core/tree/main/packages/mcp)           | An MCP server that lets an agent build the domain.                |
| [`@afora/hono`](https://github.com/afora-framework/core/tree/main/packages/hono)         | Serves the operations on Hono, with an optional OpenAPI document. |
| [`@afora/fastify`](https://github.com/afora-framework/core/tree/main/packages/fastify)   | The same on Fastify.                                              |
| [`@afora/express`](https://github.com/afora-framework/core/tree/main/packages/express)   | The same on Express 5.                                            |
| [`@afora/elysia`](https://github.com/afora-framework/core/tree/main/packages/elysia)     | The same on Elysia.                                               |
| [`@afora/ws`](https://github.com/afora-framework/core/tree/main/packages/ws)             | Operations and domain events over WebSocket.                      |
| [`@afora/drizzle`](https://github.com/afora-framework/core/tree/main/packages/drizzle)   | Repositories on Drizzle ORM (SQLite and Postgres).                |
| [`@afora/dynamodb`](https://github.com/afora-framework/core/tree/main/packages/dynamodb) | Repositories on one DynamoDB table.                               |
| [`@afora/otel`](https://github.com/afora-framework/core/tree/main/packages/otel)         | OpenTelemetry spans per command, use case and repository call.    |

### Performance

<img alt="Validations per second on the body of an API request" src="https://raw.githubusercontent.com/afora-framework/core/main/bench/results/chart.svg" width="100%">

afora validates and transforms faster than Zod 4 on most of the fourteen measured cases; checkers that compile and do not transform are faster still. The method and every case are in [Performance](https://github.com/afora-framework/core/blob/main/docs/performance.md).

### Get involved

- Questions and ideas: [Discussions](https://github.com/afora-framework/core/discussions).
- Bugs and requests: [issues](https://github.com/afora-framework/core/issues), from a template.
- Code: read [CONTRIBUTING.md](https://github.com/afora-framework/core/blob/main/CONTRIBUTING.md) first.

<div align="center">
  <sub><em>afora</em> is Portuguese for "the whole way": the guarantees hold from the request to the response.</sub>
</div>
