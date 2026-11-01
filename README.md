# BloxTracker updates

Versão atual: **3.6.0 — primeiro teste do gerenciador próprio**.

## Atualizar

No PC principal: **Atualizações → Verificar versão → Baixar atualização → Instalar e reiniciar**. Reinicie o tracker após instalar. Fonte:

```
https://raw.githubusercontent.com/danielsolzapo-dev/BloxTracker-updates/main/manifest.json
```

## Gerenciador próprio

A integração com Roblox Account Manager foi substituída por código do BloxTracker.

1. Abra **Gerenciador → Preparar login**. Instala pywebview 6.2.1 em um ambiente Python separado; requer internet, Python completo e Microsoft Edge WebView2 Runtime.
2. Clique **Adicionar conta neste PC**. Uma janela própria carrega `https://www.roblox.com/login`.
3. Entre normalmente e conclua pessoalmente qualquer verificação solicitada pelo Roblox.
4. A identificação é validada e a sessão criada nessa janela é guardada com DPAPI no Windows local.
5. Escolha **Este PC**, a conta e um Place ID; clique **Iniciar Roblox**.

Faça o primeiro teste com uma conta e uma instância do Roblox no PC principal. O cliente oficial precisa estar instalado. A abertura solicita um ticket temporário ao Roblox e o entrega ao protocolo do aplicativo no Windows; a entrada só é confirmada quando o coletor voltar a enviar dados.

### Privacidade e limites

- Não lemos sessões do navegador habitual nem do Account Manager externo.
- A senha é digitada diretamente no site oficial, sem formulário de senha no painel.
- O cookie de sessão é uma credencial: fica protegido por DPAPI em `native-sessions.json`, fora do SQLite, do ZIP público e dos backups do painel.
- Cookies e tickets não entram no estado do painel nem na sincronização central/agente. Metadados das contas e pedidos sincronizam normalmente.
- O login é feito no próprio computador onde a conta será usada. Não há transferência de sessões.
- Pedidos pendentes da integração antiga são cancelados para evitar aberturas inesperadas.
- Não há reconexão automática, controle próprio de múltiplas instâncias ou criação automática de novas contas nesta etapa.
- Se houver verificação adicional ou recusa do Roblox, é necessário novo login. Não contornamos desafios.

**Verificação:** testes simulados de login/sessão/ticket/abertura, rotas HTTP autenticadas e atualização pela rede passaram. WebView2, DPAPI e a abertura real do cliente ainda precisam ser validados no Windows do usuário. Os endpoints de autenticação e o protocolo do cliente podem mudar; esta é uma versão de teste.

Leia `GERENCIADOR.txt` para instalação e diagnóstico. Envie somente mensagens de erro, nunca cookies ou tickets.

Referências: [pywebview](https://pywebview.flowrl.com/api/), [instalação](https://pywebview.flowrl.com/guide/installation.html), [WebView2](https://developer.microsoft.com/en-us/microsoft-edge/webview2/).

`manifest.json` e `package.zip` são publicados no mesmo commit. SHA-256 verifica integridade; use somente fontes confiáveis. O cache do GitHub pode levar alguns minutos para refletir novos arquivos.
