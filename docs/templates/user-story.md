# US-NNN. Título da história

<!--
Modelo. Copie para docs/requirements/historias/US-NNN-titulo-curto.md,
usando o próximo número livre. Não reaproveite números de histórias descartadas.
Depois de criar, adicione a história ao índice em docs/requirements/README.md.
Baseado em: formato de user story da Connextra ("Como..., quero..., para...")
e critérios de aceite em Gherkin (Cucumber), no estilo Dado / Quando / Então.
-->

- Épico: <!-- ex.: Transações -->
- Prioridade: <!-- Must | Should | Could | Won't -->
- Regras de negócio: <!-- ex.: RN-01, RN-03 -->
- Requisitos não funcionais: <!-- ex.: RNF-02 -->

## História

Como [tipo de usuário], quero [ação] para [benefício].

## Critérios de aceite

<!--
Um cenário por comportamento esperado, incluindo os casos de erro.
O cenário abaixo é um exemplo: substitua pelos cenários da sua história.
-->

```gherkin
Funcionalidade: Registrar despesa
  Como usuário, quero registrar uma despesa para acompanhar meus gastos.

  Cenário: Despesa válida
    Dado que estou autenticado e tenho a conta "Carteira" com saldo de R$ 100,00
    Quando registro uma despesa de R$ 25,90 na categoria "Alimentação"
    Então o saldo da conta "Carteira" passa a ser R$ 74,10
```

## Observações

<!-- Dúvidas em aberto, casos de borda, links para protótipos. -->
