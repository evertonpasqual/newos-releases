# NewOS 2.14.1


### Corrigido
- **instalar-rsyslog.sh**:
  - o encaminhamento TCP agora declara `StreamDriver="ptcp"`. Antes, um host com `DefaultNetstreamDriver gtls` global e sem o `rsyslog-gnutls` ficava sem mandar nada, sem aviso;
  - o reinício do rsyslog não trava mais: se ele não parar em 25 s, é encerrado à força, com aviso;
  - `instalar` e `testar` conferem a conexão de verdade com o NewOS (TCP estabelecido) e mostram o erro do rsyslog quando não conecta, em vez de só "mensagem enviada".
- **NBackup (FortiGate):** a coleta recusada passa a separar três casos:
  - token aceito, mas sem permissão de backup (o perfil precisa de System = Read), com o comando do CLI;
  - Trusted Host;
  - token errado.
- **NBackup:** espaços e quebras de linha coladas junto com o token são removidos.

### Novo
- **Logs › Quem está mandando:** botão **Remover**. Apaga a cópia local de uma fonte e faz o rsyslog soltar o arquivo, então a fonte não some de vez. Se ela continuar mandando, volta com o nome atual.
