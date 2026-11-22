# 0001. Stack tecnológica

- Status: Aceita
- Data: 2026-11-20

## Contexto

- Projeto pessoal de aprendizado: um app de gestão financeira pessoal, com backend e app mobile, desenvolvido por uma pessoa.
- O objetivo principal é praticar o ciclo completo de engenharia de software: requisitos, arquitetura, backend, mobile, testes, CI/CD e operação.
- Já existe experiência com React Native.

Forças em jogo:

- Aproveitar a experiência que já existe, para que o esforço vá para engenharia e não para aprender uma linguagem nova.
- Usar a mesma linguagem no backend e no app, para compartilhar tipos, validações e regras de negócio.
- Usar ferramentas com ecossistema maduro e relevantes no mercado.
- Custo zero para começar.

## Opções consideradas

### Backend

| Opção | Prós | Contras |
| --- | --- | --- |
| **NestJS (TypeScript)** | Estrutura opinativa (módulos, injeção de dependência) que favorece arquitetura em camadas e testes; documentação extensa; mesma linguagem do app | Curva própria (decorators, DI); pode ser verboso |
| Fastify ou Express puro (TypeScript) | Leve e flexível | A estrutura tem que ser montada à mão, com mais decisões e mais risco de desorganização |
| Outra linguagem (Go, Java/Spring, .NET) | Exposição a outro ecossistema | Sem compartilhamento de código com o app; curva maior, que desvia do objetivo |

### Mobile

| Opção | Prós | Contras |
| --- | --- | --- |
| **React Native com Expo** | Experiência que já existe; builds na nuvem (EAS), atualizações OTA, Expo Router; menos configuração nativa | Dependência do ecossistema Expo; algumas bibliotecas nativas exigem *development build* |
| React Native CLI puro | Controle total da parte nativa | Mais configuração manual e manutenção de builds |
| Flutter ou nativo (Swift/Kotlin) | — | Fora do objetivo: exigiria aprender outra stack do zero |

## Decisão

| Camada | Escolha |
| --- | --- |
| Linguagem | TypeScript em modo strict em todo o projeto |
| Runtime | Node.js LTS, com a versão fixada em `.nvmrc` (26 no momento desta decisão) |
| Backend | NestJS 12 (ESM) |
| Mobile | React Native com Expo (SDK 58) e Expo Router |
| Código compartilhado | Pacote TypeScript interno, sem dependência de framework (organização no ADR 0002) |
| Testes e lint da API | Os padrões do gerador do NestJS 12: Vitest e oxlint |
| Lint do app | ESLint via `expo lint` |

### Fora do escopo desta decisão

Cada um destes itens terá um ADR próprio quando chegar a fase correspondente do guia:

- Banco de dados e ORM
- Estratégia de autenticação
- Hospedagem da API
- Bibliotecas do app (estado, formulários, armazenamento local, testes)

## Consequências

### Positivas

- Uma linguagem só nos dois lados: tipos e validações compartilhados e menos troca de contexto.
- O NestJS impõe organização em módulos e injeção de dependência, o que ajuda a praticar arquitetura em camadas e testes.
- O Expo reduz a configuração nativa e já oferece build, envio às lojas e OTA.

### Negativas e riscos

- O NestJS tem curva de aprendizado própria e pode gerar código verboso.
- Ficamos dependentes do ecossistema Expo. Se surgir uma necessidade nativa que ele não atenda, será preciso um *development build* ou módulos nativos próprios.
- O Expo lança SDKs com frequência, então upgrades regulares fazem parte da manutenção (fase 14 do guia).
- Usar uma só linguagem limita a exposição a outros ecossistemas. Isso é aceitável para o objetivo do projeto.

### Quando revisar

- Se surgir um requisito que o Expo ou o NestJS não atendam bem.
- Se o objetivo de aprendizado mudar (por exemplo, praticar outra linguagem no backend).
