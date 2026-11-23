# Requisitos não funcionais

<!--
Modelo. Copie para docs/requirements/requisitos-nao-funcionais.md.
Baseado em:
- ISO/IEC 25010:2023, modelo de qualidade de produto: as nove características usadas para classificar cada requisito.
- Volere Requirements Specification Template (James e Suzanne Robertson): cada requisito tem uma justificativa
  e um critério de aceitação mensurável ("fit criterion"). Requisito sem critério mensurável é ambíguo.

Use uma ficha por requisito. Não reaproveite IDs de requisitos removidos.
A ficha RNF-01 é um exemplo: substitua pelos requisitos do seu produto.
-->

- Versão: 0.1
- Data: AAAA-MM-DD

## Características de qualidade (ISO/IEC 25010:2023)

Use esta lista para não esquecer nenhuma dimensão. Nem todas precisam ter requisitos.

| Característica | Pergunta que ela responde |
| --- | --- |
| Adequação funcional | As funções fazem o que devem, de forma completa e correta? |
| Eficiência de desempenho | Responde rápido e usa recursos (memória, bateria, rede) com moderação? |
| Compatibilidade | Convive e troca dados com outros sistemas e versões? |
| Capacidade de interação (antiga usabilidade) | É fácil de aprender e usar, inclusive por pessoas com deficiência? |
| Confiabilidade | Fica disponível, tolera falhas e se recupera sem perder dados? |
| Segurança (*security*) | Protege dados contra acesso e alteração indevidos? |
| Manutenibilidade | É fácil de entender, testar e modificar? |
| Flexibilidade (antiga portabilidade) | Adapta-se a outros ambientes, dispositivos e versões de sistema? |
| Proteção contra danos (*safety*) | Evita causar danos às pessoas, ao negócio ou ao ambiente? |

## Requisitos

### RNF-01. Tempo de resposta da lista de transações

- **Característica:** Eficiência de desempenho
- **Requisito:** a lista de transações do mês deve carregar rapidamente.
- **Justificativa:** é a tela mais usada; lentidão nela afeta a percepção de todo o app.
- **Critério de aceitação:** 95% das chamadas a `GET /transactions` respondem em até 300 ms, com 1.000 transações no mês, no ambiente de staging.
- **Prioridade:** Must
- **Histórias relacionadas:** US-NNN

### RNF-02. <!-- título curto -->

- **Característica:** <!-- uma das nove acima -->
- **Requisito:** <!-- o que o sistema deve ter -->
- **Justificativa:** <!-- por que isso importa -->
- **Critério de aceitação:** <!-- como medir; inclua número, unidade e condição -->
- **Prioridade:** <!-- Must | Should | Could | Won't -->
- **Histórias relacionadas:** <!-- US-NNN -->

## Requisitos legais e de conformidade

<!--
Obrigações que vêm de leis ou de regras das lojas, como a LGPD e as políticas da App Store e do Google Play.
Use o mesmo formato de ficha, com a característica "Legal".
-->

## Histórico de versões

| Data | Versão | Descrição |
| --- | --- | --- |
| AAAA-MM-DD | 0.1 | Criação do documento |
