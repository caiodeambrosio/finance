# 0002. Monorepo e estrutura do repositório

- Status: Aceita
- Data: 2026-11-20

## Contexto

- Backend e app são escritos em TypeScript (ADR 0001), e há tipos e regras de negócio que os dois lados podem compartilhar.
- O projeto é desenvolvido por uma pessoa.
- A documentação deve viver junto do código (docs-as-code) e mudar no mesmo PR.
- As funcionalidades são entregues em fatias verticais, que mexem na API, no app e na documentação ao mesmo tempo.

## Opções consideradas

| Opção | Prós | Contras |
| --- | --- | --- |
| Repositórios separados (api, mobile, docs) | Isolamento total; CI de cada um mais simples | Compartilhar código exige publicar pacotes; uma funcionalidade vira vários PRs em repositórios diferentes; documentação longe do código |
| Monorepo só com workspaces, sem orquestrador | Configuração mínima | Sem cache e sem ordem automática de build entre pacotes |
| **Monorepo com pnpm workspaces + Turborepo** | Código compartilhado sem publicar nada; commits atômicos; cache e execução só do que foi afetado; configuração enxuta | Configuração inicial maior que a de um repositório simples |
| Monorepo com Nx | Mais recursos (geradores, grafo de dependências, plugins) | Mais opinativo e com mais conceitos para aprender, além do necessário para um projeto deste tamanho |

Sobre o gerenciador de pacotes: o Expo suporta monorepos com Bun, npm, pnpm e Yarn. O pnpm foi escolhido por ser rápido, economizar disco, ter workspaces nativos e pelo suporte do Expo (SDK 54 em diante) a instalações isoladas, que são o padrão do pnpm.

## Decisão

Monorepo com **pnpm workspaces** e **Turborepo**, com esta estrutura:

```
financas/
├── apps/
│   ├── api/               # NestJS
│   └── mobile/            # Expo / React Native
├── packages/
│   └── domain/            # tipos, schemas e regras de negócio puras
├── docs/
│   ├── guia-de-desenvolvimento.md
│   ├── product/           # visão, personas, concorrentes, métricas, roadmap
│   ├── requirements/      # user stories, regras de negócio, requisitos não funcionais
│   ├── design/            # links do Figma, fluxos e decisões de UX
│   ├── architecture/      # diagramas C4, modelo de dados, ameaças, estratégia de testes
│   ├── adr/               # Architecture Decision Records
│   ├── api/               # contrato OpenAPI
│   ├── release/           # política de privacidade, termos, textos das lojas, checklist
│   ├── operations/        # SLOs, alertas, runbooks/ e postmortems/
│   ├── retrospectives/    # retrospectivas de cada marco
│   └── glossary.md        # glossário do domínio
├── infra/                 # docker-compose, IaC
├── .github/workflows/     # CI/CD
├── .nvmrc
├── README.md              # visão geral e como rodar o projeto
├── package.json
├── pnpm-workspace.yaml
└── turbo.json
```

### Regras

1. `apps/` contém o que é implantado ou publicado. `packages/` contém código compartilhado, que **nunca** importa nada de `apps/`.
2. Os pacotes internos usam o escopo `@financas/*` e são referenciados com `"workspace:*"`.
3. `packages/domain` não depende de framework (nem NestJS, nem React Native) e é compilado para `dist/`, porque a API executa JavaScript compilado no Node.
4. Há um único lockfile (`pnpm-lock.yaml`) e uma única versão de `react` e `react-native` no repositório.
5. A documentação em `docs/` muda no mesmo PR que o código que ela descreve.
6. Os scripts comuns (`build`, `test`, `lint`, `dev:*`) rodam a partir da raiz, pelo Turborepo.

## Consequências

### Positivas

- Uma funcionalidade inteira (API, app, pacote compartilhado e docs) cabe em um único commit ou PR.
- Tipos e validações são definidos uma vez e usados nos dois lados.
- O Turborepo compila os pacotes na ordem certa (`domain` antes de `api`) e guarda cache dos resultados.
- O CI pode rodar só nos pacotes afetados por cada mudança.

### Negativas e riscos

- A configuração inicial é maior que a de um repositório único.
- É preciso cuidar para não ter versões duplicadas de dependências nativas do React Native.
- O CI precisa de filtros para não gerar build do app quando só a documentação mudar.
- O EAS Build precisa ser configurado levando em conta que o app está em `apps/mobile`.

### Quando revisar

- Se o número de apps ou pacotes crescer a ponto de o Turborepo não bastar (avaliar Nx).
- Se alguma parte precisar de ciclo de vida ou permissões de acesso separados (avaliar extrair para outro repositório).
