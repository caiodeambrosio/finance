# Nome do projeto

<!--
Modelo. Copie para README.md (raiz do repositório) e para apps/api/README.md e apps/mobile/README.md.
Baseado em: especificação Standard Readme (Richard Littauer), com as seções na ordem recomendada.
Obrigatórias: título, descrição curta, instalação, uso, contribuição e licença (sempre a última).
O sumário só é obrigatório em READMEs com mais de 100 linhas.

Nos READMEs dos apps, mantenha só o que é específico daquele app (variáveis de ambiente, scripts, como rodar)
e aponte para o README da raiz no resto.
-->

<!-- Descrição curta: uma frase que diga o que o projeto é. -->

## Contexto

<!-- Por que o projeto existe e o problema que resolve. Aponte para o Documento de Visão. -->

## Instalação

### Pré-requisitos

- Node.js na versão do arquivo `.nvmrc`
- pnpm
- <!-- outros pré-requisitos, conforme os ADRs (ex.: o que roda o banco local) -->

### Passos

```bash
git clone <url-do-repositório>
cd <pasta>
pnpm install
```

<!-- Variáveis de ambiente: copie o .env.example de cada app para .env e preencha. -->

## Uso

```bash
pnpm dev:api      # API em modo desenvolvimento
pnpm dev:mobile   # app mobile
pnpm test         # todos os testes
pnpm build        # build de todos os pacotes
```

## Estrutura do repositório

<!-- Resumo das pastas principais. A estrutura completa está no ADR 0002. -->

## Documentação

- Guia de desenvolvimento: `docs/guia-de-desenvolvimento.md`
- Decisões de arquitetura: `docs/adr/`
- <!-- outros documentos relevantes -->

## Contribuição

<!-- Como propor mudanças: branches, Conventional Commits, Pull Requests (ver docs/guia-de-desenvolvimento.md, seção Convenções). -->

## Licença

<!-- Nome da licença (ex.: MIT) ou "Todos os direitos reservados". -->
