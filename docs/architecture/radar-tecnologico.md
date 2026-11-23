# Radar Tecnológico

<!--
Baseado em: Technology Radar da Thoughtworks (anéis Adotar, Experimentar, Avaliar e Evitar),
agrupado por decisão a tomar, na ordem das fases do guia de desenvolvimento.
O radar sugere; quem decide é o ADR. Em caso de divergência, vale o ADR.
-->

- Versão: 0.2
- Data: 2026-11-22

## Anéis

- **Adotar:** decidido e registrado em ADR. É o que o projeto usa.
- **Experimentar:** candidato forte. Vale testar numa prova de conceito antes de decidir. Aqui estão as sugestões que antes ficavam no guia.
- **Avaliar:** vale pesquisar e comparar na seção "Opções consideradas" do ADR.
- **Evitar:** não usar neste projeto, pelo motivo indicado.

## Já adotadas

O guia de desenvolvimento não cita ADRs nem ferramentas. Esta tabela é a ponte: ela liga cada tecnologia em uso ao ADR que a decidiu. Quando um ADR for substituído, atualize a linha correspondente.

| Tecnologia | Para quê | Decisão | Mais informações |
| --- | --- | --- | --- |
| TypeScript (modo strict) | Linguagem de todo o projeto | ADR 0001 | https://www.typescriptlang.org |
| Node.js LTS | Runtime, versão fixada em `.nvmrc` | ADR 0001 | https://nodejs.org |
| NestJS 12 | Backend | ADR 0001 | https://docs.nestjs.com |
| React Native com Expo (SDK 58) | App mobile | ADR 0001 | https://docs.expo.dev · https://docs.expo.dev/guides/monorepos |
| Expo Router | Navegação do app | ADR 0001 | https://docs.expo.dev/router/introduction/ |
| Vitest e oxlint | Testes e lint da API (padrões do gerador do NestJS 12) | ADR 0001 | https://vitest.dev · https://oxc.rs/docs/guide/usage/linter |
| ESLint via `expo lint` | Lint do app | ADR 0001 | https://docs.expo.dev/guides/using-eslint/ |
| pnpm workspaces e Turborepo | Monorepo | ADR 0002 | https://pnpm.io/workspaces · https://turborepo.com/docs |
| GitHub | Repositório, CI em `.github/workflows/`, modelos de issue e de PR | ADR 0002 (prevê a pasta `.github/`) | https://docs.github.com |
| Mermaid | Diagramas dentro dos documentos | Convenção do guia | https://mermaid.js.org |

## Ferramenta de prototipação

- **Fase do guia:** 3
- **Onde registrar:** não precisa de ADR. Anote a ferramenta e o link na Especificação de UX/UI.

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| Figma | Experimentar | Padrão de mercado para protótipos navegáveis e design systems. | https://www.figma.com |
| Penpot | Avaliar | Alternativa de código aberto, que pode ser hospedada por conta própria. | https://penpot.app |

## Estilo arquitetural do backend

- **Fase do guia:** 4
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| Monolito modular | Experimentar | Um único deploy, com módulos separados por contexto de domínio (contas, transações, categorias…). Combina com os módulos do NestJS e com o tamanho do projeto. | https://martinfowler.com/bliki/MonolithFirst.html |
| Arquitetura hexagonal (portas e adaptadores) | Avaliar | Isola o domínio da infraestrutura. Pode ser combinada com o monolito modular dentro de cada módulo. | https://alistair.cockburn.us/hexagonal-architecture/ |
| Microsserviços | Evitar | A complexidade operacional (vários deploys, comunicação em rede, dados distribuídos) é desproporcional para um projeto de uma pessoa. | https://martinfowler.com/articles/microservices.html |

## Banco de dados

- **Fase do guia:** 4
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| PostgreSQL | Experimentar | Relacional, com transações e tipos numéricos exatos, o que combina com dados financeiros. É o banco com mais opções de hospedagem gerenciada. | https://www.postgresql.org |
| MySQL | Avaliar | Também relacional e muito difundido. | https://www.mysql.com |

## Acesso a dados e ORM

- **Fase do guia:** 4
- **Onde registrar:** ADR pendente (pode ser o mesmo ADR do banco de dados)

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| Prisma | Avaliar | Schema declarativo, migrações e cliente tipado gerado. | https://www.prisma.io |
| Drizzle ORM | Avaliar | Consultas próximas do SQL, com tipos em TypeScript. Também funciona com o SQLite do app, se houver modo offline. | https://orm.drizzle.team |
| TypeORM | Avaliar | Integração antiga e documentada com o NestJS, baseada em decorators. | https://typeorm.io |
| MikroORM | Avaliar | ORM com padrão Unit of Work e integração documentada com o NestJS. | https://mikro-orm.io |

## Contrato da API

- **Fase do guia:** 4 e 7
- **Onde registrar:** ADR pendente (design-first ou code-first)

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| Code-first com `@nestjs/swagger` | Experimentar | Gera o contrato OpenAPI a partir dos controllers e DTOs, então o contrato não fica desatualizado em relação ao código. | https://docs.nestjs.com/openapi/introduction |
| Design-first, com o contrato escrito à mão | Avaliar | O contrato vem antes do código e serve de acordo entre API e app. Exige validar que a implementação segue o contrato. | https://learn.openapis.org |
| Redocly CLI ou Spectral | Avaliar | Validam e aplicam regras de estilo ao arquivo OpenAPI, úteis em qualquer das duas abordagens. | https://redocly.com/docs/cli · https://stoplight.io/open-source/spectral |

## Autenticação

- **Fase do guia:** 4
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| Autenticação própria com access token de vida curta e refresh token rotativo | Experimentar | Ensina o fluxo completo e não depende de serviço externo. As boas práticas de rotação estão na RFC 9700. | https://docs.nestjs.com/security/authentication · https://datatracker.ietf.org/doc/html/rfc9700 |
| Provedor de identidade gerenciado (Auth0, Clerk, Supabase Auth, Firebase Authentication) | Avaliar | Tira do projeto o cadastro, a recuperação de senha e o login social, em troca de dependência e possível custo. | https://auth0.com · https://clerk.com · https://supabase.com/auth · https://firebase.google.com/products/auth |

## Offline e sincronização

- **Fase do guia:** 4 e 8
- **Onde registrar:** ADR pendente, se o modo offline for requisito

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| `expo-sqlite`, com sincronização própria | Experimentar | Banco local oficial do Expo. A sincronização própria é trabalhosa, mas ensina conflitos e filas de envio. | https://docs.expo.dev/versions/latest/sdk/sqlite/ |
| PowerSync | Avaliar | Serviço que mantém o SQLite do app sincronizado com o banco do servidor (inclusive PostgreSQL). | https://www.powersync.com |
| WatermelonDB | Avaliar | Banco reativo feito para apps offline. Há relatos de manutenção lenta e de ajustes necessários na nova arquitetura do React Native: confira o estado atual antes de escolher. | https://watermelondb.dev |

## Quadro de tarefas

- **Fase do guia:** 5
- **Onde registrar:** não precisa de ADR. Coloque o link do quadro no README da raiz, seção Contribuição.

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| GitHub Projects | Experimentar | Fica junto do repositório e liga cartões a issues e PRs. | https://docs.github.com/en/issues/planning-and-tracking-with-projects |
| Linear | Avaliar | Rápido e bem integrado ao GitHub. | https://linear.app |
| Trello | Avaliar | Quadro Kanban simples. | https://trello.com |

## Formatação de código

- **Fase do guia:** 6
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| Prettier | Experimentar | Padrão de mercado. O gerador do NestJS 12 já o instala em `apps/api`. | https://prettier.io |
| Oxfmt | Avaliar | Do mesmo projeto do oxlint (já adotado), compatível com o Prettier e bem mais rápido. Entrou em beta em fevereiro de 2026: confira se já há versão estável. | https://oxc.rs/docs/guide/usage/formatter |
| Biome | Avaliar | Formatador e linter num só, também compatível com o estilo do Prettier. | https://biomejs.dev |

## Hooks de commit

- **Fase do guia:** 6
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| Husky + lint-staged | Experimentar | Combinação mais difundida: roda lint e formatação só nos arquivos alterados. | https://typicode.github.io/husky/ · https://github.com/lint-staged/lint-staged |
| commitlint | Experimentar | Valida as mensagens no padrão Conventional Commits. | https://commitlint.js.org |
| Lefthook | Avaliar | Alternativa única, rápida e sem dependência de Node para os hooks. | https://github.com/evilmartians/lefthook |

## Banco de dados local

- **Fase do guia:** 6
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| Docker Compose | Experimentar | Sobe o banco com um comando e uma configuração versionada em `infra/`. | https://docs.docker.com/compose/ |
| Podman | Avaliar | Alternativa ao Docker, sem daemon, compatível com arquivos Compose. | https://podman.io |

## Validação de entrada

- **Fase do guia:** 7 e 8
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| Zod (via Standard Schema do NestJS 12) | Experimentar | O NestJS 12 aceita schemas Standard Schema direto nas rotas. Os mesmos schemas podem ficar em `packages/domain` e ser usados pela API e pelos formulários do app. | https://zod.dev · https://docs.nestjs.com/techniques/validation |
| class-validator | Avaliar | Abordagem tradicional do NestJS, com DTOs e decorators. Continua sendo o padrão documentado, mas não serve para compartilhar validação com o app. | https://docs.nestjs.com/techniques/validation |
| Valibot ou ArkType | Avaliar | Alternativas compatíveis com Standard Schema, com pacotes menores. | https://valibot.dev · https://arktype.io |

## Logs estruturados

- **Fase do guia:** 7
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| pino (com nestjs-pino) | Experimentar | Logs em JSON, rápidos e com contexto de requisição. | https://github.com/iamolegga/nestjs-pino |
| Logger nativo do NestJS com saída JSON | Avaliar | Sem dependência extra. Pode bastar no começo. | https://docs.nestjs.com/techniques/logger |

## Proteções HTTP

- **Fase do guia:** 7
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| `@nestjs/throttler` | Experimentar | Limite de requisições oficial do NestJS. | https://docs.nestjs.com/security/rate-limiting |
| helmet | Experimentar | Define cabeçalhos de segurança HTTP. Recomendado na documentação do NestJS. | https://docs.nestjs.com/security/helmet |
| CORS nativo do NestJS | Experimentar | Já vem no framework; só precisa de configuração. | https://docs.nestjs.com/security/cors |

## Health check

- **Fase do guia:** 7
- **Onde registrar:** ADR pendente, ou só a seção 8 do Documento de Arquitetura

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| `@nestjs/terminus` | Experimentar | Módulo oficial, com verificações prontas de banco, memória e disco. | https://docs.nestjs.com/recipes/terminus |
| Endpoint próprio simples | Avaliar | Uma rota que responde 200 pode bastar no começo. | — |

## Gerenciamento de estado

- **Fase do guia:** 8
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| TanStack Query (estado vindo da API) | Experimentar | Cache, nova tentativa e sincronização de dados do servidor sem código manual. | https://tanstack.com/query |
| Zustand (estado local) | Experimentar | Pequeno e simples para o estado que só existe no app. | https://zustand.docs.pmnd.rs |
| SWR (estado vindo da API) | Avaliar | Alternativa mais enxuta ao TanStack Query. | https://swr.vercel.app |
| Redux Toolkit e RTK Query | Avaliar | Solução completa para estado local e da API, com mais estrutura e mais código. | https://redux-toolkit.js.org |
| Jotai (estado local) | Avaliar | Estado em pequenas unidades independentes (átomos). | https://jotai.org |
| Context do React | Avaliar | Nativo do React. Serve para pouco estado que muda pouco. | https://react.dev/reference/react/useContext |

## Formulários

- **Fase do guia:** 8
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| React Hook Form | Experimentar | Muito difundido e integra com schemas de validação, inclusive Zod. | https://react-hook-form.com |
| TanStack Form | Avaliar | Alternativa com tipagem forte e suporte a Standard Schema. | https://tanstack.com/form |

## Cliente HTTP gerado do OpenAPI

- **Fase do guia:** 8
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| openapi-typescript + openapi-fetch | Avaliar | Gera só os tipos e usa um cliente fetch leve. A opção mais enxuta. | https://openapi-ts.dev |
| Hey API (`@hey-api/openapi-ts`) | Avaliar | Gera um SDK com uma função por operação, com plugins. | https://heyapi.dev |
| Orval | Avaliar | Além do cliente, gera hooks de TanStack Query, schemas Zod e mocks. | https://orval.dev |

## Armazenamento seguro de tokens

- **Fase do guia:** 8
- **Onde registrar:** ADR pendente (pode ser o mesmo ADR de autenticação)

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| `expo-secure-store` | Experimentar | Usa o Keychain no iOS e o Keystore no Android. | https://docs.expo.dev/versions/latest/sdk/securestore/ |
| AsyncStorage para tokens | Evitar | Guarda os dados sem criptografia. Serve para preferências, não para credenciais. | https://react-native-async-storage.github.io/async-storage/ |

## Biometria

- **Fase do guia:** 8
- **Onde registrar:** ADR pendente, ou só a seção 8 do Documento de Arquitetura

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| `expo-local-authentication` | Experimentar | Módulo oficial do Expo para Face ID, Touch ID e biometria do Android. | https://docs.expo.dev/versions/latest/sdk/local-authentication/ |

## Testes da API e do domínio

- **Fase do guia:** 9
- **Onde registrar:** Estratégia de Testes, com ADR para o que não estiver no ADR 0001

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| Vitest (API) | Adotar | Padrão do gerador do NestJS 12. | ADR 0001 · https://vitest.dev |
| Vitest (`packages/domain`) | Experimentar | Mesma ferramenta da API, sem nada novo para aprender. | https://vitest.dev |
| supertest | Experimentar | Testes de ponta a ponta da API. O gerador do NestJS 12 já o instala e usa no teste e2e de exemplo. | https://www.npmjs.com/package/supertest |
| Testcontainers | Experimentar | Sobe um banco real e descartável para cada execução dos testes de integração. | https://node.testcontainers.org |

## Testes do app

- **Fase do guia:** 9
- **Onde registrar:** Estratégia de Testes, com ADR

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| jest-expo + React Native Testing Library | Experimentar | Combinação documentada pelo Expo para testes de componentes. | https://docs.expo.dev/develop/unit-testing/ |
| Maestro | Experimentar | Testes de ponta a ponta em YAML, sem alterar o build. Tem sido a escolha mais comum em projetos Expo novos. | https://maestro.dev |
| Detox | Avaliar | Testes de ponta a ponta com sincronização interna com o React Native. Exige mais configuração no Expo. | https://wix.github.io/Detox/ |

## Segurança de dependências e código

- **Fase do guia:** 9
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| Dependabot | Experimentar | Nativo do GitHub: avisa e abre PRs para dependências vulneráveis ou desatualizadas. | https://docs.github.com/en/code-security/dependabot |
| CodeQL | Experimentar | Análise estática de segurança nativa do GitHub. | https://codeql.github.com |
| Renovate | Avaliar | Alternativa ao Dependabot, mais configurável e com bom suporte a monorepos. | https://docs.renovatebot.com |
| Semgrep | Avaliar | Análise estática com regras fáceis de escrever. | https://semgrep.dev |

## Build e distribuição do app

- **Fase do guia:** 10
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| EAS Build, EAS Submit e EAS Update | Experimentar | Serviços do Expo para build na nuvem, envio às lojas e atualizações OTA. | https://docs.expo.dev/eas/ |
| Builds locais (Xcode e Android Studio) com fastlane | Avaliar | Sem serviço externo, mas exige Mac para iOS e mais configuração. | https://docs.expo.dev/guides/local-app-development/ · https://fastlane.tools |

## Versionamento e changelog

- **Fase do guia:** 10
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| Changesets | Experimentar | Feito para monorepos: cada PR declara o impacto e a ferramenta gera versões e changelog por pacote. | https://github.com/changesets/changesets |
| release-please | Experimentar | Gera versões e changelog a partir de Conventional Commits, por PR de release. | https://github.com/googleapis/release-please |
| semantic-release | Avaliar | Publica automaticamente a cada merge, também a partir de Conventional Commits. | https://semantic-release.gitbook.io |

## Hospedagem da API

- **Fase do guia:** 11
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| Render | Avaliar | Plataforma gerenciada, deploy a partir do GitHub. | https://render.com |
| Fly.io | Avaliar | Roda containers perto dos usuários, com mais controle. | https://fly.io |
| Railway | Avaliar | Plataforma gerenciada, com banco de dados no mesmo painel. | https://railway.com |
| AWS | Avaliar | Mais flexível e mais complexa. Bom para praticar infraestrutura, com risco de custo. | https://aws.amazon.com |

## Banco gerenciado

- **Fase do guia:** 11
- **Onde registrar:** ADR de hospedagem

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| Banco do próprio provedor de hospedagem | Avaliar | Menos peças: API e banco no mesmo lugar. | — |
| Neon | Avaliar | PostgreSQL gerenciado, com branches de banco para testes. | https://neon.tech |
| Supabase | Avaliar | PostgreSQL gerenciado, com serviços extras (autenticação, armazenamento). | https://supabase.com |

## Infraestrutura como código

- **Fase do guia:** 11 (opcional)
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| Terraform | Experimentar | O mais difundido no mercado. | https://developer.hashicorp.com/terraform |
| OpenTofu | Avaliar | Alternativa de código aberto, compatível com o Terraform. | https://opentofu.org |
| Pulumi | Avaliar | Infraestrutura escrita em TypeScript, a mesma linguagem do projeto. | https://www.pulumi.com |

## Monitoramento de erros e telemetria

- **Fase do guia:** 13
- **Onde registrar:** ADR pendente

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| Sentry | Experimentar | Erros e crashes no app e na API, com SDKs para React Native e NestJS. | https://sentry.io |
| SDK do OpenTelemetry para Node.js | Experimentar | Padrão aberto para logs, métricas e traces, sem prender a um fornecedor. | https://opentelemetry.io/docs/languages/js/ |
| NestJS Observe (`@nestjs/observe`) | Avaliar | Instrumentação oficial do NestJS 12, ligada a um painel hospedado. Só cobre a API. | https://docs.nestjs.com/observability/overview |
| Firebase Crashlytics | Avaliar | Relatórios de crash no app, gratuitos. | https://firebase.google.com/products/crashlytics |

## Analytics de produto

- **Fase do guia:** 13
- **Onde registrar:** ADR pendente. Confira a coerência com a Política de Privacidade.

| Opção | Anel | Por quê | Mais informações |
| --- | --- | --- | --- |
| PostHog | Avaliar | Analytics de produto com opção de código aberto e hospedagem própria. | https://posthog.com |
| Google Analytics for Firebase | Avaliar | Gratuito e integrado ao ecossistema Firebase. | https://firebase.google.com/products/analytics |

## Histórico de versões

| Data | Versão | Descrição |
| --- | --- | --- |
| 2026-11-22 | 0.1 | Criação do radar com as sugestões retiradas do guia e as alternativas de cada uma |
| 2026-11-22 | 0.2 | Coluna de links na tabela "Já adotadas", que passa a ser a ponte entre o guia e os ADRs |
