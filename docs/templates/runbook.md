# Runbook: título do procedimento

<!--
Modelo. Copie para docs/operations/runbooks/titulo-curto.md (um arquivo por procedimento).
Baseado em: estrutura usual de runbooks em SRE: gatilho, pré-requisitos, passos com o resultado esperado,
verificação, rollback e escalonamento.

Escreva para alguém que nunca viu o sistema e está resolvendo um problema às 3 da manhã:
comandos completos, prontos para copiar, e o resultado esperado de cada passo.
-->

- Serviço: <!-- ex.: API -->
- Última revisão: AAAA-MM-DD
- Testado em: <!-- data do último ensaio do procedimento -->

## Quando usar

<!-- O gatilho: um alerta específico, um sintoma ou uma tarefa planejada (ex.: restaurar backup, deploy manual). -->

## Pré-requisitos

- Acesso a: <!-- painel do provedor, banco, CI -->
- Ferramentas: <!-- CLIs necessárias -->

## Passos

1. <!-- O que fazer -->

   ```bash
   # comando
   ```

   Resultado esperado: <!-- o que deve aparecer -->

2. <!-- próximo passo -->

## Verificação

- [ ] <!-- ex.: o health check da API responde 200 -->
- [ ] <!-- ex.: a taxa de erros voltou ao normal no monitoramento -->

## Rollback

<!-- Como desfazer o procedimento se ele piorar a situação. -->

## Escalonamento

<!-- Quem acionar ou onde pedir ajuda se o procedimento não resolver (ex.: suporte do provedor de hospedagem). -->

## Referências

<!-- SLO relacionado, alertas que disparam este runbook, post-mortems anteriores. -->
