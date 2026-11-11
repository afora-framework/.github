<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/afora-framework/core/main/.github/assets/afora-banner-dark.png">
  <img alt="afora — Simple to write. Built to hold." src="https://raw.githubusercontent.com/afora-framework/core/main/.github/assets/afora-banner-light.png" width="100%">
</picture>

[English](https://github.com/afora-framework/.github/blob/main/profile/README.md) &nbsp;·&nbsp; **Português (Brasil)**

### Simple to write. Built to hold.

<em>Simples de escrever. Feito para durar.</em>

[![npm](https://img.shields.io/npm/v/@afora/core?color=E4572E&label=%40afora%2Fcore)](https://www.npmjs.com/package/@afora/core)
[![Licença MIT](https://img.shields.io/badge/licen%C3%A7a-MIT-4E7C5B)](https://github.com/afora-framework/core/blob/main/LICENSE)
[![Standard Schema V1](https://img.shields.io/badge/Standard%20Schema-V1-21504F)](https://standardschema.dev)
[![Antes da 1.0](https://img.shields.io/badge/status-antes%20da%201.0-F0B44C)](https://github.com/afora-framework/core/blob/main/VERSIONING.md)

</div>

**O afora é um framework domain-first para backends em TypeScript.** Você declara o que são suas entidades, seus casos de uso e sua API, e o runtime mantém as garantias que são fáceis de esquecer. Quem quer que escreva o código, você ou seu agente, elas se mantêm.

Modele o domínio; o runtime mantém as invariantes. Construído sobre [TypeBox](https://github.com/sinclairzx81/typebox), com [Standard Schema](https://standardschema.dev) em todo campo, no Bun e no Node.

### Por que afora

Um backend HTTP escrito por um agente, ou com pressa, costuma quebrar as mesmas poucas garantias. No afora, cada uma faz parte do runtime:

| O que costuma quebrar                       | O que o afora faz                                                                  |
| ------------------------------------------- | ---------------------------------------------------------------------------------- |
| Um hash de senha aparece numa resposta      | Uma propriedade `sensitive` é mascarada pelo `toJSON()` em qualquer profundidade.  |
| Campos extras no corpo da requisição passam | Chaves não declaradas são rejeitadas em qualquer profundidade; a API responde 400. |
| Um erro de negócio volta como 500           | Os erros sabem sua camada e viram problem+json com o status certo.                 |
| Um e-mail duplicado é gravado duas vezes    | Chaves `unique` são garantidas pelo repositório; a violação é um 409.              |

### Para você e para o seu agente

**Experiência de desenvolvimento.** Quatro declarações até uma API CRUD. Tipos que seguem o modelo: `findByEmail` existe porque `email` é único. Qualquer servidor (Hono, Fastify, Express, Elysia) e qualquer banco (em memória, Drizzle, DynamoDB).

**Experiência do agente.** A aplicação inteira é dado: um `afora.json` declara as entidades, os casos de uso em passos e a API HTTP. Um servidor MCP deixa o agente escrevê-lo, o codegen o transforma em TypeScript que você revisa, e o runtime segura o que o agente esquece.

### Uma olhada rápida

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

o mesmo e-mail de novo
-> 409 application/problem+json  { "title": "UserAlreadyExists", "layer": "use-case", ... }
```

O exemplo completo, e o mesmo app como `afora.json`, estão no [quick start](https://github.com/afora-framework/core#quick-start).

### Pacotes

| Pacote                                                                                   | O que faz                                                              |
| ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| [`@afora/core`](https://github.com/afora-framework/core)                                 | O framework: das propriedades às saídas.                               |
| [`@afora/codegen`](https://github.com/afora-framework/core/tree/main/packages/codegen)   | De `afora.json` para TypeScript, e de uma aplicação de volta à spec.   |
| [`@afora/mcp`](https://github.com/afora-framework/core/tree/main/packages/mcp)           | Um servidor MCP para um agente construir o domínio.                    |
| [`@afora/hono`](https://github.com/afora-framework/core/tree/main/packages/hono)         | Serve as operações no Hono, com documento OpenAPI opcional.            |
| [`@afora/fastify`](https://github.com/afora-framework/core/tree/main/packages/fastify)   | O mesmo no Fastify.                                                    |
| [`@afora/express`](https://github.com/afora-framework/core/tree/main/packages/express)   | O mesmo no Express 5.                                                  |
| [`@afora/elysia`](https://github.com/afora-framework/core/tree/main/packages/elysia)     | O mesmo no Elysia.                                                     |
| [`@afora/ws`](https://github.com/afora-framework/core/tree/main/packages/ws)             | Operações e eventos de domínio por WebSocket.                          |
| [`@afora/drizzle`](https://github.com/afora-framework/core/tree/main/packages/drizzle)   | Repositórios sobre Drizzle ORM (SQLite e Postgres).                    |
| [`@afora/dynamodb`](https://github.com/afora-framework/core/tree/main/packages/dynamodb) | Repositórios em uma tabela do DynamoDB.                                |
| [`@afora/otel`](https://github.com/afora-framework/core/tree/main/packages/otel)         | Spans OpenTelemetry por comando, caso de uso e chamada de repositório. |

### Performance

<img alt="Validações por segundo no corpo de uma requisição de API" src="https://raw.githubusercontent.com/afora-framework/core/main/bench/results/chart.svg" width="100%">

O afora valida e transforma mais rápido que o Zod 4 na maioria dos catorze casos medidos; validadores que compilam e não transformam são mais rápidos ainda. O método e todos os casos estão em [Performance](https://github.com/afora-framework/core/blob/main/docs/performance.md).

### Participe

- Dúvidas e ideias: [Discussions](https://github.com/afora-framework/core/discussions).
- Bugs e pedidos: [issues](https://github.com/afora-framework/core/issues), a partir de um template.
- Código: leia o [CONTRIBUTING.md](https://github.com/afora-framework/core/blob/main/CONTRIBUTING.md) antes.

<div align="center">
  <sub><em>afora</em>, como em "mundo afora": as garantias valem do começo ao fim.</sub>
</div>
