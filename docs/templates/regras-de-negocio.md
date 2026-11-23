# Regras de negócio

<!--
Modelo. Copie para docs/requirements/regras-de-negocio.md.
Baseado em: catálogo de regras de negócio de Karl Wiegers e Joy Beatty (livro "Software Requirements"),
com as colunas ID, definição, tipo, estática ou dinâmica e origem.

Uma regra de negócio é uma política, lei ou cálculo do domínio que existe independentemente do software.
As histórias citam as regras que aplicam pelo ID (RN-NN). Não reaproveite IDs de regras removidas.
As linhas da tabela são exemplos: substitua pelas regras do seu produto.
-->

- Versão: 0.1
- Data: AAAA-MM-DD

## Catálogo

| ID | Regra | Tipo | Estática ou dinâmica | Origem |
| --- | --- | --- | --- | --- |
| RN-01 | O saldo de uma conta é a soma das receitas e transferências recebidas, menos as despesas e transferências enviadas. | Cálculo | Estática | Domínio financeiro |
| RN-02 | Uma transferência entre contas do mesmo usuário não altera o patrimônio total dele. | Fato | Estática | Domínio financeiro |
| RN-03 | <!-- descreva a regra --> | <!-- tipo --> | <!-- estática ou dinâmica --> | <!-- origem --> |

## Tipos de regra

- **Fato:** algo verdadeiro sobre o domínio. Ex.: toda transação pertence a exatamente uma conta.
- **Restrição:** algo que o sistema deve impedir ou exigir. Ex.: o valor de uma transação deve ser maior que zero.
- **Ativador de ação:** uma condição que dispara uma ação. Ex.: se o gasto de uma categoria passar de 80% do orçamento, avisar o usuário.
- **Inferência:** um fato novo que se conclui de outros. Ex.: uma despesa com vencimento passado e não paga está atrasada.
- **Cálculo:** uma fórmula. Ex.: o saldo de uma conta (RN-01).

## Estática ou dinâmica

- **Estática:** dificilmente muda (leis da contabilidade, definições).
- **Dinâmica:** pode mudar com o tempo ou por decisão de produto (limites, prazos, percentuais). Regras dinâmicas pedem atenção extra: evite fixá-las no código sem configuração.

## Histórico de versões

| Data | Versão | Descrição |
| --- | --- | --- |
| AAAA-MM-DD | 0.1 | Criação do documento |
