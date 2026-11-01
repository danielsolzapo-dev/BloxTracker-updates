# BloxTracker updates

Versão atual: **3.8.0 — seis visuais e aviso de verificação manual**.

## Novidades 3.8

- **Aparência** na navegação: Clássico (visual anterior), Aurora, Órbita, Luz, Terminal e Horizonte. Seletor com prévias e preferência por navegador. Aurora é o padrão.
- Electro procura também o sprite Electric. Após atualizar, execute o coletor novamente pelo carregador (coletor 3.2).
- A janela de login reconhece caminhos de desafio ou iframes visíveis identificáveis de CAPTCHA e avisa no Gerenciador local. Aguarda resolução pessoal na janela oficial e continua a validação da sessão; não resolve nem envia desafios a terceiros. Formatos diferentes podem não ser detectados. Prazo de login permanece 9 minutos.
- Reconexão, metas, recursos e agentes mantidos. Testes de atualização LAN, sessão, reconexão e busca de sprites passaram; verificação real no Windows ainda depende do usuário.


## Atualizar

No central: **Atualizações → Verificar versão → Baixar atualização → Instalar e reiniciar**. Atualize também os agentes e reinicie o tracker neles. Fonte:

```
https://raw.githubusercontent.com/danielsolzapo-dev/BloxTracker-updates/main/manifest.json
```

## Reconexão automática

No **Gerenciador**, selecione PC, conta salva e jogo. Com o coletor online e o PID vinculado, configure **Reconexão automática** e ative para a conta selecionada.

- Padrão: intervalo de **60 segundos**, até **3 tentativas**. Configurável: 45–3600 segundos e 1–10 tentativas.
- Por padrão, só reabre depois de verificar que o processo identificado terminou. Falta de dados sozinha não confirma queda.
- A opção **Reiniciar também quando parar de enviar dados** é separada e desligada por padrão. Prazo mínimo 120 segundos; inicial 180 segundos. Ela pode fechar uma instância ainda aberta cujo coletor parou.
- **Fechar Roblox pelo painel**, desvincular o PID ou excluir a conta pausa a política. Fechar pelo X do Windows é tratado como saída, não como pausa do painel.
- **Meta atingida** interrompe; **manutenção** suspende. Encerrar manutenção permite monitorar novamente.
- **PC sem contato**, identidade desconhecida ou falta de permissão não permitem uma nova abertura automática.
- Abertura incerta ou falha de login exige revisão manual. Não repetimos solicitações sem confirmação.
- O contador persiste e zera após dois minutos de dados estáveis. Para reativar, confira o PC e use o botão na política.
- O processo é identificado por PID, criação, conta e sessão; nunca é encerrado por nome de executável.
- O agente confere a configuração atual antes de executar e novamente imediatamente antes de abrir o jogo. Uma pausa posterior não desfaz uma abertura já concluída.

Mantenha central e agentes abertos pelo Iniciar.bat. Evite relançadores concorrentes para a mesma conta. Sessões de login precisam estar cadastradas localmente em cada PC; não há transferência de credenciais.

## Gerenciador próprio

Não depende do Roblox Account Manager externo. Em cada PC Windows: **Preparar login → Adicionar conta neste PC**. A janela própria carrega o site oficial do Roblox; conclua pessoalmente as verificações solicitadas.

O componente usa pywebview 6.2.1 e Microsoft Edge WebView2 Runtime. A sessão criada nessa janela é validada e protegida com DPAPI em `native-sessions.json`. Cookies e tickets não entram no painel, no protocolo de rede do tracker, no ZIP ou no backup. O cliente oficial do Roblox precisa estar instalado.

## Verificação

Testes com central/agente reais do tracker e processos/abertura simulados passaram: queda, manutenção, autorização, recuperação pelo coletor e pausa por fechamento manual. Testes cobrem tentativas, intervalo, reset, sessão/PID alterados, revisão por resultado incerto e preservação da atualização pela rede. A reconexão com processos reais ainda precisa ser validada no Windows do usuário.

Consulte `GERENCIADOR.txt` para operação e limites. Envie só mensagens de erro, nunca cookies ou tickets.

`manifest.json` e `package.zip` são publicados juntos. SHA-256 verifica integridade; a fonte distribui código executável e precisa ser confiável. O cache do GitHub pode levar alguns minutos para refletir os novos arquivos.
