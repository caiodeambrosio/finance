# SLOs: nome do serviço

<!--
Modelo. Copie para docs/operations/slo.md.
Baseado em: documento de SLO de exemplo do Google SRE Workbook, com as seções visão geral do serviço,
SLIs e SLOs, justificativa, orçamento de erro, e esclarecimentos e ressalvas.

SLI (indicador) é o que se mede; SLO (objetivo) é a meta para esse indicador numa janela de tempo.
Os valores da tabela são exemplos: defina os seus a partir dos requisitos não funcionais.
-->

- Versão: 0.1
- Data: AAAA-MM-DD

## Visão geral do serviço

<!-- O que o serviço faz, quem depende dele e de quais componentes ele depende. -->

## SLIs e SLOs

| Categoria | SLI (como medir) | SLO (meta) | Janela |
| --- | --- | --- | --- |
| Disponibilidade | Proporção de requisições à API que não retornam erro 5xx | 99,5% | 28 dias |
| Latência | Proporção de requisições respondidas em até 500 ms | 99% | 28 dias |
| <!-- categoria --> | <!-- indicador --> | <!-- meta --> | <!-- janela --> |

## Justificativa

<!-- Por que essas metas: de onde vieram os números e o que ainda não foi validado com dados reais de uso. -->

## Orçamento de erro

<!--
O orçamento de erro de cada SLO é 100% menos a meta (ex.: 99,5% de disponibilidade = 0,5% de requisições com erro na janela).
Descreva o que acontece quando o orçamento acaba (ex.: pausar novas funcionalidades e priorizar confiabilidade).
-->

## Esclarecimentos e ressalvas

<!-- Limitações da medição (ex.: o que conta como erro, requisições que o monitoramento não vê). -->

## Histórico de versões

| Data | Versão | Descrição |
| --- | --- | --- |
| AAAA-MM-DD | 0.1 | Criação do documento |
