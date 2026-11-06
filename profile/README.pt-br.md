<div align="center">

<img width="2560" height="640" alt="Afora Framework Banner" src="https://github.com/user-attachments/assets/c7df04bf-316e-461c-aa60-34f6bb0cd3b6" />

<br/>

[English](https://github.com/afora-framework/.github/blob/main/profile/README.md) &nbsp;•&nbsp; **Português (Brasil)**

<br/>

### Além dos limites convencionais. Projetado para software moderno e guiado pelo domínio.

[![GitHub Org](https://img.shields.io/badge/organização-afora--framework-242938?style=for-the-badge&logo=github&logoColor=white)](https://github.com/afora-framework)
[![Licença](https://img.shields.io/badge/licença-MIT-8FB59A?style=for-the-badge)](https://github.com/afora-framework/core)
[![Status](https://img.shields.io/badge/status-desenvolvimento%20ativo-E08A63?style=for-the-badge)](https://github.com/afora-framework/core)

</div>

---

### 🌿 Sobre o Afora Framework

O **Afora** é um framework moderno em TypeScript projetado para **Modelagem de Domínio e Domain-Driven Design (DDD)** robusto e expressivo sobre [TypeBox](https://github.com/sinclairzx81/typebox). Criado desde o início para integrar-se com qualquer consumidor de [Standard Schema V1](https://standardschema.dev) (como Hono, tRPC e TanStack Form), o Afora oferece ergonomia e rigor técnico às fronteiras e regras de negócio da sua aplicação.

Longe de ser apenas um validador genérico de dados, o Afora estrutura suas entidades com invariantes estritas, proteção automática de dados sensíveis, fluxos tipados de alteração, exceções com consciência de camadas arquiteturais e ferramentas nativas para agentes de IA.

---

### ✨ Pilares Fundamentais

- 🧩 **Modelagem de Domínio e Invariantes**: Declare propriedades (`Email`, `Slug`, `Password`), blueprints e registros que validam e normalizam valores, rejeitando propriedades não declaradas em qualquer profundidade.
- 🔒 **Proteção de Dados Sensíveis**: Campos marcados como `sensitive` (como `Password`) são mascarados automaticamente pelo `toJSON()` em qualquer nível, prevenindo vazamento acidental em logs ou respostas de APIs.
- 🏛️ **Entidades, Repositórios e Use Cases**: `entityOf` gerencia identidade, timestamps e eventos de domínio; `repositoryOf` gera métodos tipados de consulta (como `findBy<Key>`); use cases orquestram a lógica com injeção de dependências substituíveis.
- 🛡️ **Exceções em Camadas**: Sistema de exceções consciente da camada de origem (`Property`, `Record`, `Repository`, `UseCase`), acumulando um histórico de rastreio (`trace`) conforme cruzam a aplicação.
- ⚡ **Standard Schema e Multi-Runtime**: Conformidade nativa com Standard Schema V1 em todos os campos. Otimizado para [Bun](https://bun.sh) e Node.js (>= 22), carregando sem atrito em navegadores e Workers sem importação prematura de módulos criptográficos.
- 🤖 **Pronto para IA e Declarativo**: Servidor MCP nativo (`@afora/mcp`) e gerador de código (`@afora/codegen`) que permitem a desenvolvedores e agentes de IA modelar e construir sistemas de domínio de forma colaborativa.

---

### 📦 Ecossistema e Repositórios

| Pacote / Repositório | Descrição | Status |
| :--- | :--- | :--- |
| [**`core`** (`@afora/core`)](https://github.com/afora-framework/core) | Motor central de domínio: Properties, Blueprints, Records, Entities, Repositories, Use Cases e Playground interativo local | 🚧 Desenvolvimento Ativo |
| [**`@afora/codegen`**](https://github.com/afora-framework/core/tree/main/packages/codegen) | Especificações declarativas de domínio (`afora.json`) com geração de código TypeScript idiomática e bidirecional | 🚧 Desenvolvimento Ativo |
| [**`@afora/mcp`**](https://github.com/afora-framework/core/tree/main/packages/mcp) | Servidor Model Context Protocol (MCP) que habilita agentes de IA a consultar o catálogo, validar e gerar domínios Afora | 🚧 Desenvolvimento Ativo |

---

### 🚀 Playground Interativo

O `@afora/core` inclui um playground local integrado, equipado com Monaco Editor e serviços de linguagem TypeScript, para experimentar modelos de domínio, testar invariantes e inspecionar saídas mascaradas em tempo real:

```bash
bun add @afora/core
bun run playground
```

---

### 🤝 Contribuição e Comunidade

Desenvolvedores, arquitetos de software e entusiastas de código aberto são muito bem-vindos para construir o futuro do Afora Framework!

- 💡 **Discussões e Ideias**: Compartilhe ideias, proponha RFCs ou tire dúvidas nas discussões e issues dos repositórios.
- 🛠️ **Pull Requests**: Veja as tarefas e issues abertas no [repositório core](https://github.com/afora-framework/core).
- 🐞 **Reporte de Problemas**: Encontrou um bug ou tem uma sugestão de recurso? Abra uma issue no repositório correspondente.

---

<div align="center">
  <sub>Desenvolvido com dedicação pela comunidade <strong>Afora Framework</strong>.</sub>
</div>
