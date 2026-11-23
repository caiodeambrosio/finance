# Estratégia de Testes

<!--
Modelo. Copie para docs/architecture/estrategia-de-testes.md.
Baseado em:
- ISO/IEC/IEEE 29119-3 (documentação de testes): níveis e tipos de teste, critérios de entrada, saída e conclusão,
  dados e ambientes de teste, automação e gestão de defeitos. Simplificado para um projeto pequeno: a norma separa
  estratégia, plano e relatórios em documentos distintos, e aqui eles ficam juntos.
- Pirâmide de testes (Mike Cohn): muitos testes unitários, menos de integração e poucos de ponta a ponta.

Na coluna Ferramenta, use só ferramentas já decididas: as da API vêm do ADR 0001, as demais de ADRs próprios.
-->

- Versão: 0.1
- Data: AAAA-MM-DD

## 1. Objetivos e escopo

<!-- O que os testes precisam garantir e o que fica fora (ex.: testes de carga só depois do MVP). -->

## 2. Riscos cobertos

<!-- Os riscos que justificam o esforço de teste, com o vínculo para requisitos e ameaças. -->

| Risco | Como os testes cobrem | Vínculo |
| --- | --- | --- |
| Cálculo de saldo errado | Testes unitários das regras de domínio | RN-01 |
| <!-- risco --> | <!-- como --> | <!-- RN, RNF ou AM --> |

## 3. Níveis de teste

| Nível | O que cobre | Ferramenta | Onde fica | Quando roda |
| --- | --- | --- | --- | --- |
| Unitário | Regras de domínio e funções puras | <!-- ADR --> | Ao lado do código (`*.spec.ts`) | A cada commit e no CI |
| Integração (API) | API com banco real | <!-- ADR --> | `apps/api/test/` | No CI |
| Ponta a ponta (API) | Endpoints completos | <!-- ADR --> | `apps/api/test/` | No CI |
| Componentes (mobile) | Telas e componentes isolados | <!-- ADR --> | Ao lado do código | No CI |
| Ponta a ponta (mobile) | Fluxos críticos no app | <!-- ADR --> | <!-- pasta usada pela ferramenta escolhida --> | Antes de cada release |

## 4. Tipos de teste

- [ ] Funcional: os critérios de aceite das histórias
- [ ] Regressão: a suíte toda roda no CI a cada PR
- [ ] Segurança: dependências, análise estática e as mitigações do modelo de ameaças
- [ ] Desempenho: os critérios mensuráveis dos requisitos não funcionais
- [ ] Acessibilidade: os itens da especificação de UX

## 5. Critérios de entrada, saída e conclusão

- **Para abrir um PR:** testes do que mudou escritos e passando localmente.
- **Para fazer merge:** CI verde (lint, typecheck, testes, build).
- **Para liberar uma versão:** fluxos críticos de ponta a ponta passando, sem bugs abertos de gravidade alta.

## 6. Dados de teste

<!-- Como os dados são criados (fábricas, seeds) e a regra de nunca usar dados reais de usuários. -->

## 7. Ambientes de teste

<!-- Local, CI e staging: o que roda em cada um. -->

## 8. Automação e CI

<!-- Quais suítes rodam em cada evento (push, PR, merge na main, release). -->

## 9. Gestão de defeitos

<!-- Bugs viram issues com o modelo de relato de bug. Defina o que é gravidade alta, média e baixa. -->

## 10. Métricas

<!-- Ex.: cobertura das regras de domínio, testes instáveis, tempo do pipeline. -->

## Histórico de versões

| Data | Versão | Descrição |
| --- | --- | --- |
| AAAA-MM-DD | 0.1 | Criação do documento |
