# BloxTracker updates

Versão atual: **3.11.0 — cadastro por tentativa e cofre local**.

## Novidades 3.11

- **Gerenciador → Criar conta**: uma tentativa por clique. Informe sua data de nascimento correta, prefixo e confirme que leu/aceita os termos. O tracker gera usuário/senha e tenta preencher/enviar o formulário na janela oficial do Roblox deste PC.
- CAPTCHA ou verificação identificável interrompe os cliques automáticos. Formulário desconhecido, recusa ou ausência de confirmação também interrompem; não há solver, proxy nem repetição automática. A janela pode ser usada pessoalmente para concluir ou fechada.
- **Criar manualmente** abre o cadastro oficial sem preencher/enviar. A aceitação dos termos e as verificações são realizadas pelo usuário no próprio site.
- **Pastas → Contas criadas**: cofre local, com estados separados para credencial preparada, submetida, CAPTCHA, recusa, sem confirmação, criada e informada manualmente. Só uma sessão validada do usuário gerado confirma a criação.
- Senhas ocultas; **Mostrar senha por 30s** exige clique. Fechar o cofre ou ocultar a página esconde a senha. Credenciais manuais podem ser guardadas sem alegar validação da conta.
- `created-accounts.json` usa DPAPI do usuário Windows. Credenciais não entram no SQLite, estado público, LAN, exportação, backup ou pacote GitHub. Não há transferência de cofre entre PCs. Bloqueio entre processos protege as gravações.
- Após sucesso, a sessão validada é guardada no gerenciador local. Dados de nascimento são consumidos pelo helper e removidos do registro após esse consumo. Dados de cadastro não são passados pela linha de comando.

**Validação:** testes simulados de preenchimento, uma submissão, parada no CAPTCHA sem nova submissão, data alterada, cofre, rotas autenticadas e atualização LAN passaram. Não criamos contas reais nos testes. O formulário atual, WebView2 e DPAPI precisam de validação no Windows; se o formulário mudou, use cadastro manual. Prazo de 9 minutos por janela.


## Novidades 3.10

- **Parar operação** por seleção ou grupo: cancela esperas e pedidos ainda na fila do central, pausa reconexões e agendamentos e interrompe sequências. Instâncias continuam abertas por padrão; fechar jogos identificados é uma opção separada. Pedidos já entregues ao Windows podem terminar.
- A pausa afeta só as contas escolhidas. Agendamentos compartilhados são separados para preservar as outras contas. **Retomar operação** libera novas ações e horários futuros; horários passados são marcados como perdidos. Esperas canceladas e reconexões não são retomadas automaticamente.
- **Fila de início**: posição por PC, motivo atual e espera mínima estimada quando calculável. Carregamento e disponibilidade podem prolongar o tempo; não é um horário garantido.
- **Reiniciar gradualmente** no grupo: fixa PID, criação e sessão, fecha uma instância, confirma a saída, espera os dados antigos expirarem e abre no destino salvo. Só avança quando o coletor volta com nova sessão e identidade correta.
- A leitura do processo pelo agente pode chegar depois dos dados do coletor; a sequência aguarda essa confirmação. Mudança real de PID/sessão, falha ou ausência de confirmação interrompe para revisão. Fechamentos não são repetidos automaticamente.
- O reinício pausa reconexões e horários do grupo. Ao concluir, novas ações ficam liberadas; retome os horários e reative reconexões separadamente. Etapas sem confirmação por mais de 5 minutos exigem revisão. Mantenha central/agentes/coletor ativos.

Consulte GERENCIADOR.txt. Os testes usam processos e abertura simulados; a execução real destas novas ações ainda precisa de validação no Windows.


## Novidades 3.9

- Gerenciador com abas Contas e grupos, Fila de início, Computadores e Agendamentos.
- Seleção de contas em vários PCs, grupos salvos e início em lote. Cada PC precisa das suas sessões locais já cadastradas.
- Capacidade padrão: 6 instâncias monitoradas, intervalo de 20 segundos e 1 carregamento por vez. Ajustável por PC: 1–100 instâncias, 5–600 segundos e 1–5 carregamentos simultâneos. Processos que o tracker desconhece não entram na contagem.
- Prioridade de 0 a 9 por conta, destino (Place ID/Job ID) salvo e confirmação do coletor antes da próxima abertura. Agentes atualizados informam o ID esperado para conferir a identidade.
- Pausa de fila por PC e pausa de reconexão por seleção, grupo ou PC. Fechar pelo painel também cancela esperas da conta; pedidos já entregues podem terminar.
- Agendamentos pontuais de início ou fechamento. Central e agentes precisam estar abertos. Horários perdidos por mais de 5 minutos não executam. Fechamento fica preso ao PID, criação e sessão escolhidos e depende de dados recentes no momento de executar.
- Diagnóstico de Windows, login, protocolo Roblox e contato. Estado de sessão informa credencial salva ou necessidade de conferir login; não faz validação contínua online. Verificações humanas continuam manuais.
- Aberturas incertas bloqueiam novas admissões no PC até revisão. Liberar a fila não repete o pedido antigo. Reativar reconexão reconhece os resultados incertos anteriores da mesma conta.

**Validação 3.9:** fila por prioridade/capacidade, grupos, destinos, identidade, agendamentos perdidos, fechamento preso à instância e atualização LAN passaram. Teste com central/agente reais do tracker confirmou ordem, espera pelo coletor e fechamento agendado, com processos e abertura simulados. Falta validar estas novas funções no Windows real.


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
