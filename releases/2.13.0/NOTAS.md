# NewOS 2.13.0


### Novo
- **Módulo NBackup** (Sistema › Módulos): backup das configurações de switches, roteadores e firewalls.
  - **Fabricantes:** Cisco IOS/IOS-XE (com *enable*), Cisco NX-OS, Huawei VRP e MikroTik RouterOS por SSH; FortiGate pela API de backup, com token.
  - **Coleta diária** no horário escolhido, com o botão "Coletar agora".
  - **Histórico em git** no diretório que você indicar: um disco montado em Armazenamento › Discos ou uma pasta existente.
  - **Versões e diferenças:** só vira versão nova quando a configuração muda de verdade. Relógio, "last change" e as senhas que a FortiGate recifra a cada exportação ficam de fora. A tela mostra a diferença entre duas versões, a configuração completa e o download.
  - **S3:** mesmo bucket e mesma senha do backup do sistema, na pasta `<servidor>/rede/`, cifrado. Retenção própria e "Restaurar o histórico do S3".
  - **Backup do sistema:** passa a levar os equipamentos e as credenciais.
- **Segurança do NBackup:**
  - **Credenciais:** cifradas, só o root lê; nunca voltam para a tela.
  - **Coleta sem privilégio:** a conexão com os equipamentos roda como o usuário `nbackup`, sem shell.
  - **Chave fixada:** a chave SSH (ou o certificado da API) de cada equipamento é fixada no primeiro acesso. Se mudar, a coleta para e o painel pede para aceitar a chave nova.
  - **Sem porta de entrada:** nenhuma porta é aberta no NewOS; quem conecta é ele.
  - **Acesso restrito:** ver e baixar a configuração é só para administradores e fica na auditoria.
- **Métricas para o Prometheus** (node_exporter): situação, último sucesso e última mudança de cada equipamento.
