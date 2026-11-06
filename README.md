# BloxTracker updates

Versão atual **3.18.0 — identidade SK Rejoin e central dos computadores**.

- Novo visual preto, branco e dourado, com a arte do SK Rejoin. Aparência permite trocar para OLD ou os temas anteriores.
- Comparar selecionadas mostra de 2 a 6 contas lado a lado, com nível, saldos, mar, raça, frutas lendárias/míticas, estilos, acessórios e metas.
- Resumo das metas mostra objetivos ativos, concluídos, próximos de concluir e que precisam de atenção.
- Alertas no painel ficam agrupados por computador e mantêm os controles de abrir conta e dispensar.
- Perfis de recursos incluem largura/altura da janela e usam os comandos existentes de RAM e CPU com confirmação individual.
- Central dos PCs mostra vagas do gerenciador, RAM disponível do Windows, versão do tracker e botão para atualizar um agente específico.
- Central de atualizações lista computador, versão instalada, versão de destino e mensagem de cada agente.

Atualize o central e os agentes para receber a nova telemetria de memória. O pacote preserva os arquivos de configuração e dados locais pelo atualizador existente. Vagas consideram as instâncias acompanhadas pelo gerenciador.

Validado com comparação e troca de temas no navegador, perfis e telemetria em testes, atualização LAN autenticada com download/instalação/reinício reais do tracker em Linux e processos simulados. Medição de RAM e abertura do Roblox ainda precisam de validação no Windows.

## Novidades 3.17

- **Frutas guardadas na tabela de contas:** mostra ícones apenas das lendárias e míticas.
- **Ver conta → Inventário:** mantém todas as frutas, incluindo comuns, incomuns e raras.
- Total de frutas guardadas, filtros, regras e metas continuam considerando o inventário completo.
- Raridade enviada pelo coletor tem prioridade. Quando ausente, nomes conhecidos são usados; frutas não classificadas continuam no inventário completo.
- O coletor também passa a encaminhar raridade textual disponível no catálogo de frutas. O filtro por nomes funciona com os dados já existentes.

**Validação:** classificação de lendárias/míticas, exclusão de baixas/desconhecidas, prioridade de raridade explícita e sintaxe do painel passaram. Inventário detalhado e contagens globais não foram filtrados.



## Novidades 3.16

- CPU dos processos Roblox amostrada aproximadamente a cada 2 segundos em segundo plano, independente da frequência de consulta do navegador/coletor.
- Normalização por tempo decorrido e processadores lógicos ativos, incluindo grupos de processadores do Windows. Intervalos longos, negativos e leituras sem base não viram zero.
- Telemetria dos agentes no heartbeat a cada 3 segundos, restrita a conta/sessão/PID/criação correspondentes. A idade relativa evita diferenças de relógio entre os PCs. Não renova artificialmente a conexão do coletor.
- Cartões mostram **CPU dos Roblox**, cobertura e idade da amostra. Processos duplicados não são somados duas vezes e cobertura incompleta deixa o total Aguardando.
- O navegador conserva seu intervalo de atualização; a leitura pode chegar com atraso. É a soma dos Roblox monitorados, não o uso total do Windows nem uma promessa de coincidir com a métrica do Gerenciador de Tarefas.

**Validação:** testes numéricos de cargas conhecidas, intervalos inválidos, agregação parcial/duplicada e heartbeat HTTP autenticado com relógio deslocado passaram; CPU/fechamento e atualização LAN também validados. Comparação com um Roblox real no Windows ainda precisa ser feita no PC de origem. Atualize central e agentes.



## Novidades 3.15

- **Studio**, uma identidade visual própria: cinza escuro, azul discreto, navegação por operação/sistema e maior densidade de informação.
- Busca e filtro por PC em uma barra, atalhos Todas/Online/Sem sinal e filtros avançados recolhíveis. Os mesmos controles e valores são preservados ao trocar o visual.
- Indicadores compactos e resumo dos computadores com menos espaço ocupado.
- Detalhes da conta em painel lateral no Studio, mantendo a lista visível ao fundo. Todas as abas e funções anteriores permanecem.
- **Aparência → OLD** retorna ao tema ativo antes desta reformulação. Os seis temas anteriores continuam disponíveis, além de Studio e OLD.
- Studio aparece na primeira abertura após a atualização; a escolha posterior fica salva por navegador. Não altera contas, metas, processos ou configuração LAN.

**Validação:** painel, filtros rápidos, troca Studio/OLD e detalhes laterais conferidos no navegador com dados de demonstração. Pacote e atualização autenticada central/agente passaram.



## Novidades 3.14

- **Ver conta → Recursos → Proporção e tamanho da janela**: informe largura e altura da área interna do jogo em pixels (ex.: 800×600, 960×540 ou 600×600).
- **Aplicar e manter tamanho** confere o tamanho a cada 2 segundos no PID/sessão atuais. **Desativar ajuste** preserva o tamanho atual e libera o redimensionamento.
- Controle por conta, local ou agente atualizado. Pinagem de PID, criação e sessão; comando expirável e confirmação no PC de origem. Mudança de PID exige nova aplicação.
- A manutenção preserva janelas minimizadas; o clique explícito pode restaurar a janela. Não altera resolução do monitor, FOV nem escala de renderização. Requer Roblox em modo janela; Windows/Roblox podem impor tamanho mínimo.
- API de janela assíncrona, identificação da janela pelo PID e confirmação limitada no tempo. Falhas interrompem a manutenção e aparecem no painel.

**Validação:** tamanho de área interna com bordas, HWND correto, minimização e PID reutilizado testados com Win32 simulado. Comando HTTP/LAN, confirmação, rejeição de alvo antigo, CPU, fechamento e atualização dos agentes passaram. Formulário conferido no navegador. Redimensionamento real, DPI e limites do Roblox ainda precisam ser validados no Windows.



## Novidades 3.13

- **Envio em lote**: selecione ou arraste até 20 arquivos; cada arquivo mantém seu pedido separado. Limite de 25 MiB por arquivo. Erro na solicitação interrompe o restante do lote, sem repetir pedidos aceitos.
- **Favoritos de pastas por PC**, até 30 por computador, salvos no navegador atual.
- **Busca por nome** nos itens da página carregada (até 200), sem busca recursiva.
- **Copiar entre PCs**: prepare o arquivo na origem, escolha o PC/unidade/pasta de destino e confirme a cópia. O central intermedia e verifica SHA-256; o navegador não precisa baixar o arquivo.
- Progresso percentual no envio navegador-central; tamanho, etapas e confirmação de gravação separados por pedido. O trecho central-agente mostra estado, sem percentual de rede.
- Sobrescrita continua desligada por padrão. Limites, cache, isolamento por agente e proteção das credenciais do tracker permanecem.

**Validação:** testes de integridade, cache adulterado recusado, cópia de agente para central, upload/download e atualização LAN passaram com serviços reais em Linux. Favoritos, busca e fluxo de cópia conferidos no navegador com dados de demonstração. Windows e seleção real de arquivos ainda precisam de validação nos seus PCs.



## Novidades 3.12

- Nova aba **Arquivos**: selecione o computador, unidade e pasta; navegue no PC central e nos agentes registrados.
- Envie um arquivo escolhido no navegador para o destino selecionado; baixe arquivos do agente e salve no PC do navegador.
- Criação de pastas e botão para enviar um ZIP do tracker atual, sem configuração de rede, sessões ou senhas. O envio não instala nem executa o conteúdo.
- Até **25 MiB por arquivo**, cache de 250 MiB, 20 pedidos ativos, cancelamento e conferência SHA-256. Arquivos existentes só são substituídos com a opção explícita de sobrescrita.
- Pedidos expiram em 15 minutos; cache e registros encerrados são limpos após 1 hora. Cancelar não desfaz uma gravação já concluída.
- Transporte pela conexão LAN autenticada existente, com autorização por PC. Painel e agentes precisam estar abertos e atualizados; Roblox não precisa estar aberto.
- Credenciais internas conhecidas do tracker não aparecem nesta aba. O acesso às demais pastas segue as permissões do usuário Windows.

**Validação:** testes de upload/download binário em serviços central/agente reais, isolamento de chaves, cancelamento, não sobrescrita, integridade, pasta e pacote sanitizado passaram em Linux. Interface conferida no navegador com dados de demonstração. Unidades, permissões e gravação atômica no Windows precisam de validação nos seus PCs.



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
