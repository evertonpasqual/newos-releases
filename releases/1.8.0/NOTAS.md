# NewOS 1.8.0


### Novo
- **Sistema › Terminal** (como o do Cockpit): shell de **root** deste
  servidor no navegador, sem precisar de SSH. Só para contas com perfil de
  administrador; para abrir, o painel pede a senha de novo (e o código do
  MFA, se a pessoa usar), o que vale por 30 minutos. Fonte ajustável,
  aparência (escuro, claro, NewIO), "Nova sessão". O shell roda fora do
  sandbox do painel (um serviço transitório do systemd). Abrir e fechar vão
  para a auditoria e para o journal (`newos-terminal`). O terminal fecha
  sozinho sem digitação pelo tempo de sessão inativa e ao sair do painel.
  Terminal no navegador: xterm.js 5.5 (MIT), servido pelo próprio painel.
- **Sessão inativa**: quem deixa o painel aberto sem usar é desconectado
  sozinho (padrão 15 min, ajustável em Usuários › Contas: 5 a 120 min). Um
  minuto antes aparece o aviso com contagem e "Continuar conectado"; as
  telas que se atualizam sozinhas não contam como uso; com várias abas, a
  que está em uso mantém a sessão. A tela de login diz o motivo.
