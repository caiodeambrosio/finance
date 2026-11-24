# Documento de Visão

<!--
Baseado em: documento Visão do RUP (declaração do problema e declaração de posição do produto)
e Vision and Scope Document de Karl Wiegers (escopo, fora do escopo, restrições e premissas).

A visão define o problema, para quem é o produto e os limites do escopo.
Requisitos detalhados ficam na Especificação de Requisitos (docs/requirements/).
-->

- Versão: 0.2
- Data: 2026-11-24

## Declaração do problema

- **O problema de:** não ter, em um só lugar, o histórico dos gastos de cada mês, a projeção dos meses seguintes (contas fixas, assinaturas, parcelas que ainda vão vencer) e o acompanhamento do mês atual em relação ao que foi planejado. Como a maior parte dos gastos do dia a dia passa pelo cartão de crédito, só se sabe quanto foi gasto quando a fatura fecha, e aí já não dá para ajustar.
- **afeta:** pessoas que recebem uma renda mensal, concentram os gastos no cartão de crédito, têm compras parceladas e dividem algumas despesas com outras pessoas (cônjuge, familiares, colegas de casa).
- **cujo impacto é:** surpresas na fatura, metas por categoria estouradas sem perceber, parcelas e recorrências esquecidas que comprometem os meses seguintes, dificuldade de saber quanto cada pessoa deve reembolsar e de separar dinheiro para a reserva financeira. Manter tudo isso em planilha é trabalhoso e propenso a erro.
- **uma solução bem-sucedida seria:** um app em que o planejamento do mês (renda, metas por categoria, reserva) é definido uma vez; as contas recorrentes e as parcelas aparecem sozinhas nos meses seguintes; a fatura do cartão pode ser importada várias vezes ao longo do mês, com os gastos classificados automaticamente; e a qualquer momento é possível ver quanto ainda se pode gastar no mês, quanto é custo fixo e quanto é variável, e quanto cada pessoa deve pagar.

## Declaração de posição do produto

- **Para:** pessoas que controlam as próprias finanças, usam o cartão de crédito como principal meio de pagamento e dividem parte dos gastos com outras pessoas
- **que:** precisam saber, durante o mês, se estão dentro do planejado e como os compromissos já assumidos afetam os próximos meses
- **o Finanças é:** um app mobile de planejamento e acompanhamento de gastos mensais
- **que:** projeta os meses futuros a partir das recorrências e dos parcelamentos, classifica automaticamente os gastos da fatura importada e mostra quanto ainda resta para gastar em cada categoria
- **diferentemente de:** planilhas mantidas à mão e apps de controle financeiro centrados em registrar transações uma a uma
- **nosso produto:** é organizado em torno do mês (passado, atual e futuros) e da fatura do cartão, aprende a classificar os gastos com base nos meses anteriores e trata a divisão de despesas como parte do planejamento, e não como um app separado

## Objetivos e métricas de sucesso

| Objetivo | Métrica | Meta |
| --- | --- | --- |
| Saber durante o mês se os gastos estão dentro do planejado | Toques a partir da abertura do app até ver quanto ainda se pode gastar no mês e por categoria | No máximo 1 toque (informação na tela inicial do mês atual) |
| Reduzir o esforço de registrar os gastos do cartão | Tempo para importar uma fatura e classificar os gastos que o sistema não reconheceu | Menos de 2 minutos para uma fatura parcial típica |
| Classificar a maioria dos gastos sem intervenção | Percentual de gastos importados classificados automaticamente, depois de 3 meses de histórico | Pelo menos 80% |
| Reimportar a fatura sem duplicar nem perder lançamentos | Diferença entre os lançamentos registrados de uma fatura e os da última versão importada dela | Zero |
| Prever os meses seguintes | Diferença entre o total projetado para um mês futuro e o total real quando ele chega, considerando só recorrências e parcelas | Zero (o que é previsível deve estar na projeção) |
| Acertar contas com quem divide gastos | Valor que cada pessoa deve no mês disponível sem cálculo manual | 100% dos meses |
| Substituir a planilha | Meses consecutivos usando só o app | 6 meses |

## Partes interessadas e usuários

| Parte interessada | Papel | Interesse |
| --- | --- | --- |
| Usuário principal | Usa o app, decide o escopo e desenvolve o projeto | Controlar os gastos com pouco esforço e praticar o ciclo completo de engenharia de software |
| Pessoas com quem os gastos são divididos | Afetadas, mas não usam o app no MVP | Saber com clareza quanto devem pagar a cada mês |

### Persona: quem organiza as finanças da casa

- Recebe uma renda mensal fixa e, às vezes, receitas extras (bônus, 13º, trabalhos avulsos).
- Paga quase tudo no cartão de crédito, incluindo assinaturas e compras parceladas. Algumas contas (aluguel, condomínio, energia) são pagas fora do cartão, com vencimento em dia fixo.
- Divide parte das despesas com outra pessoa (por exemplo, o cônjuge) e às vezes compra no próprio cartão algo que é inteiramente da outra pessoa, que reembolsa a parcela todo mês.
- Quer separar todo mês um valor para a reserva financeira.
- Hoje acompanha tudo em planilha e pelo app do banco, e só percebe que gastou demais quando a fatura fecha.

## Análise de concorrentes

| Alternativa | Pontos fortes | Pontos fracos | O que levar para o nosso produto |
| --- | --- | --- | --- |
| Planilha própria | Flexível, sob medida, sem custo | Trabalho manual para lançar gastos, replicar recorrências e parcelas e calcular divisões; ruim no celular | O modelo mental de "uma aba por mês" e a liberdade de definir as próprias categorias |
| Apps de controle financeiro pessoal (ex.: Mobills, Organizze) | Categorias, orçamentos, cartões de crédito, gráficos; maduros e com boa usabilidade | Centrados em lançar transações; a divisão de gastos com outras pessoas não é o foco | Orçamento por categoria e controle de fatura do cartão |
| App do banco ou do cartão | Gastos aparecem quase em tempo real, sem digitar nada | Vê só aquele banco; não tem metas pessoais, projeção de meses futuros nem divisão de gastos | A fatura do banco como fonte dos dados do dia a dia, por importação |
| Apps de divisão de despesas (ex.: Splitwise) | Calculam quem deve a quem | Não fazem orçamento nem projeção; exigem lançar os gastos em outro app | Divisão por percentual ou valor integral e saldo por pessoa |

## Escopo do MVP

### Dentro do escopo

1. **Planejamento do mês:** renda mensal, metas de gasto por categoria e valor destinado à reserva financeira. A soma das metas tem que caber na renda.
2. **Receitas extras:** receitas avulsas lançadas em um mês específico.
3. **Gastos recorrentes fora do cartão:** descrição, valor, dia de vencimento e categoria; aparecem automaticamente nos meses seguintes.
4. **Cartão de crédito:** uma fatura por banco. Gastos recorrentes no cartão (assinaturas), compras parceladas (exibidas com o status da parcela no mês, ex.: 2/5, e projetadas nos meses seguintes) e gastos do dia a dia, cadastrados à mão ou trazidos pela importação da fatura.
5. **Importação da fatura:** importar a fatura do cartão nos formatos dos dois bancos: em CSV, aberta ou fechada, quantas vezes for preciso no mesmo mês, e em PDF, depois do fechamento. Cada lançamento vira um registro: um gasto do dia a dia, uma parcela ou a ocorrência de um gasto recorrente já cadastrado. Uma compra parcelada é criada na primeira vez que aparece e reconhecida nas faturas seguintes. O pagamento da fatura anterior, que também vem no arquivo, não conta como gasto. Importar de novo não duplica o que já foi registrado, seja por uma importação anterior, seja por cadastro manual. Um serviço de classificação atribui a categoria de cada lançamento com base nos lançamentos anteriores e pede ao usuário que classifique o que não reconheceu.
6. **Divisão de gastos:** cadastrar as pessoas com quem se divide e, para cada gasto, informar se ele é dividido (e em que proporção) ou se é inteiramente de outra pessoa. Mostrar quanto o usuário paga e quanto cada pessoa deve no mês.
7. **Visão mês a mês:** abas com os meses passados, o mês atual e alguns meses à frente. Em cada mês: total previsto e realizado, custo fixo e custo variável, comparação com as metas por categoria e quanto ainda se pode gastar.

### Fora do escopo

- Conexão direta com bancos (Open Finance) e leitura automática de SMS e notificações. Os dados do cartão entram por importação da fatura (CSV ou PDF) ou por cadastro manual.
- Importação de outros formatos ou layouts de fatura além dos dois do MVP, e a partir de capturas ou gravações da tela. São candidatas para depois do MVP.
- Cartões adicionais: a fatura de cada banco é tratada como um todo, sem separar os gastos por portador.
- Contas para as pessoas com quem se divide gastos: elas são só nomes cadastrados pelo usuário, sem acesso ao app.
- Controle de pagamento dos reembolsos (marcar quem já pagou, cobrar).
- Investimentos, rendimento da reserva e patrimônio.
- Múltiplas moedas.
- Lembretes e notificações de vencimento.
- Versão web ou desktop.
- Funcionamento offline com sincronização (pode ser reavaliado na fase de arquitetura).

## Restrições e premissas

### Restrições

- Projeto pessoal, desenvolvido por uma pessoa, com custo zero para começar.
- Stack definida no [ADR 0001](../adr/0001-stack-tecnologica.md) e organização do repositório no [ADR 0002](../adr/0002-monorepo-e-estrutura-do-repositorio.md).
- Valores monetários em reais (BRL), sempre como inteiros em centavos.
- Dados financeiros são dados pessoais; o tratamento segue a LGPD.
- Os arquivos de fatura não têm um identificador por lançamento, e pode haver lançamentos idênticos legítimos (mesma data, estabelecimento e valor). Evitar duplicidade não pode depender só do conteúdo de cada linha.
- A fatura aberta muda até o fechamento: lançamentos pendentes podem mudar de valor ou sumir entre uma importação e outra.
- O CSV não informa a qual fatura pertence; o vencimento aparece só no nome do arquivo. O PDF traz o vencimento.
- O PDF é um documento feito para impressão: a leitura depende do layout do banco e quebra se ele mudar.

### Premissas

- O app começa com um único usuário (quem o desenvolve), mas cada usuário só acessa os próprios dados, para que ele possa ser publicado nas lojas depois.
- Há uma fatura por banco. Cartões adicionais não são considerados, e a coluna de portador do CSV é ignorada.
- Um dos bancos permite baixar a fatura em CSV a qualquer momento, inclusive antes do fechamento. Esse CSV (data da compra, estabelecimento, portador, valor e parcela) é um dos dois formatos que o MVP importa.
- Outro banco só permite baixar a fatura depois do fechamento, em PDF. O PDF tem texto (não é imagem escaneada) e traz o total de cada grupo de lançamentos, o que permite conferir a leitura. Nesse cartão, o usuário que quiser acompanhar os gastos durante o mês os cadastra à mão, e a importação da fatura fechada concilia esses registros.
- Um gasto no cartão pertence ao mês da fatura em que é cobrado, e não ao mês da compra.
- A descrição de um mesmo estabelecimento se repete de forma parecida entre faturas, o que permite classificar por semelhança. A exceção são os pagamentos feitos por intermediários (carteiras digitais que aparecem com o próprio nome ou com o nome do usuário): a descrição não indica a categoria, e o usuário terá que classificá-los.
- Gastos recorrentes (dentro e fora do cartão) são custo fixo; gastos do dia a dia são custo variável.

## Questões em aberto

Pontos a resolver na fase de requisitos (fase 2). As questões resolvidas ficam riscadas, com o lugar onde a resposta foi registrada.

1. ~~**Formato da fatura**~~ Resolvida na versão 0.2: CSV no banco que libera a fatura aberta e PDF no outro, com uma fatura por banco (ver [Restrições e premissas](#restrições-e-premissas)).
2. ~~**Parcelas na importação**~~ Resolvida na versão 0.2: a importação cria e reconhece compras parceladas (ver [Escopo do MVP](#dentro-do-escopo)).
3. **Fixo ou variável:** compras parceladas contam como custo fixo (compromisso já assumido) ou variável?
4. **Reserva e metas:** a regra é "soma das metas + reserva ≤ renda"? As receitas extras de um mês aumentam o limite das metas daquele mês ou vão para a reserva?
5. **Metas variando no tempo:** a renda e as metas são as mesmas todo mês até serem alteradas, ou podem ser diferentes em cada mês? Alterar uma meta muda os meses passados?
6. **Divisão:** a divisão é sempre por percentual (ex.: 50/50) ou também por valor fixo? Pode envolver mais de duas pessoas no mesmo gasto?
7. **Gasto de responsabilidade de outra pessoa:** ele entra nas metas e no custo do usuário, ou só aparece no valor a receber daquela pessoa?
8. **Horizonte:** quantos meses à frente o app deve mostrar?
9. **Categorias:** o app traz categorias prontas ou o usuário cria todas?
10. **Recorrências que mudam de valor:** como tratar uma assinatura que sobe de preço ou uma conta de energia que varia todo mês?
11. ~~**Fatura do banco que só a libera depois do fechamento**~~ Resolvida na versão 0.2: PDF, e a importação de PDF entra no MVP (ver [Escopo do MVP](#dentro-do-escopo)).
12. ~~**Portador**~~ Resolvida na versão 0.2: cartões adicionais não são considerados, e a fatura é tratada por banco (ver [Fora do escopo](#fora-do-escopo)).
13. **Estornos:** um estorno (valor negativo na fatura) abate o gasto na categoria da compra original, no mês em que aparece? E se o estorno de uma compra parcelada vier de uma vez, enquanto as parcelas continuam aparecendo nas faturas seguintes?
14. **Encargos do banco:** juros, multa e IOF cobrados na fatura viram gastos de uma categoria própria? Contam nas metas e no custo fixo ou no variável?

## Histórico de versões

| Data | Versão | Descrição |
| --- | --- | --- |
| 2026-11-23 | 0.1 | Criação do documento |
| 2026-11-24 | 0.2 | Resolve as questões 1, 2, 11 e 12 (importação por CSV e PDF, uma fatura por banco sem cartões adicionais, importação que cria e reconhece parcelamentos), registra as limitações dos arquivos de fatura e abre as questões 13 e 14 |
