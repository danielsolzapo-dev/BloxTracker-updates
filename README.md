# BloxTracker updates

Versão atual: **3.5.1**.

## Atualizar

No central: **Atualizações → Verificar versão → Baixar atualização → Instalar e reiniciar**. Depois atualize os agentes selecionados.

```
https://raw.githubusercontent.com/danielsolzapo-dev/BloxTracker-updates/main/manifest.json
```

## Correção do instalador (3.5.1)

Fecha explicitamente as conexões SQLite do backup para evitar arquivos ocupados no Windows. Falhas agora mostram tipo, código e nome do arquivo. Em instalações antigas, feche e reabra o tracker antes de instalar; após concluir, feche e abra novamente para carregar o instalador corrigido.

## Gerenciador — primeira etapa

A nova aba **Gerenciador** inicia contas sob demanda no PC local ou em outro PC da rede. Usa a API documentada do Roblox Account Manager 3.x (`GetAccounts` e `LaunchAccount`). O Account Manager precisa estar aberto e a conta precisa estar cadastrada e autenticada no PC escolhido.

Configure uma vez em cada PC Windows, na aba Gerenciador do tracker local: porta, senha da API e integração ativa. Sincronize as contas e faça a abertura pelo central. Consulte **GERENCIADOR.txt** no pacote para as configurações do Account Manager.

- O agente recebe pedidos mesmo sem Roblox aberto.
- Um pedido não é repetido automaticamente quando a resposta é incerta.
- A entrada é confirmada quando o coletor enviar dados; mantenha o coletor no Auto Execute.
- A senha da API é protegida com DPAPI e permanece no PC configurado.
- Senhas Roblox e cookies não são coletados. Não acessamos GetCookie nem GetAccountsJson.
- **Esta etapa ainda não tem reconexão automática nem transferência de sessões entre PCs.**

Testado com API RAM simulada e agentes reais do tracker na rede de teste. A compatibilidade com a instalação Windows/Account Manager do usuário precisa ser validada nela.

API: https://ic3w0lf22.gitbook.io/roblox-account-manager

## Publicação

`manifest.json` e `package.zip` são enviados no mesmo commit. SHA-256 verifica a integridade; a fonte distribui código executável e precisa ser confiável. Configurações e sessões ficam fora do pacote. O cache do GitHub pode levar alguns minutos para refletir os arquivos novos.
