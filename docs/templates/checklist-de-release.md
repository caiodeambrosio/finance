# Checklist de release: versão X.Y.Z

<!--
Modelo. Copie para docs/release/release-X.Y.Z.md (um arquivo por versão publicada nas lojas).
Baseado em: requisitos de publicação da App Store Connect (Apple) e do Play Console (Google),
incluindo os limites de caracteres dos textos das lojas. Os limites podem mudar: confira a ajuda oficial de cada loja.
-->

- Data prevista: AAAA-MM-DD
- Versão: X.Y.Z (Versionamento Semântico)

## Antes do build

- [ ] Versão atualizada no app e no `CHANGELOG.md`
- [ ] Todas as histórias da versão concluídas, segundo a Definition of Done
- [ ] Migrações de banco aplicadas em staging
- [ ] Nenhum bug aberto de gravidade alta

## Testes

- [ ] Fluxos críticos de ponta a ponta passando
- [ ] Build distribuído pelo TestFlight (iOS) e pela faixa de teste interno (Google Play)
- [ ] Testado em pelo menos um aparelho real de cada plataforma

## Privacidade

- [ ] Política de privacidade publicada em URL pública e atualizada
- [ ] Formulário App Privacy (App Store) preenchido de acordo com a política
- [ ] Formulário Data safety (Google Play) preenchido de acordo com a política

## Textos das lojas

### App Store

| Campo | Limite | Texto |
| --- | --- | --- |
| Nome | 30 caracteres | |
| Subtítulo | 30 caracteres | |
| Texto promocional | 170 caracteres | |
| Palavras-chave | 100 bytes, separadas por vírgula | |
| Descrição | 4.000 caracteres | |
| Novidades desta versão | 4.000 caracteres | |

### Google Play

| Campo | Limite | Texto |
| --- | --- | --- |
| Nome do app | 30 caracteres | |
| Descrição curta | 80 caracteres | |
| Descrição completa | 4.000 caracteres | |
| Notas da versão | 500 caracteres | |

## Imagens

- [ ] Ícone
- [ ] Capturas de tela nos tamanhos exigidos por cada loja
- [ ] Imagem de destaque (Google Play)

## Publicação

- [ ] Liberação gradual configurada (lançamento em fases na App Store, lançamento gradual no Google Play)
- [ ] Monitoramento de erros acompanhado nas primeiras horas
- [ ] SLOs conferidos depois da liberação

## Depois da release

- [ ] Tag da versão criada no Git
- [ ] Problemas encontrados registrados como issues
