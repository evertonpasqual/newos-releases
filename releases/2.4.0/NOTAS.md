# NewOS 2.4.0


### Novo
- Firewall › Proteção › **País / região**: liberar só alguns países (ex.: só
  Brasil) ou bloquear países. Vale na WAN e nos redirecionamentos de porta;
  redes internas nunca são bloqueadas; as faixas de IP são baixadas na hora e
  atualizadas toda semana. Recusa a alteração se o IP de quem está no painel
  ficaria bloqueado.
- Usuários › Contas: **senha dos usuários do Linux** (root e newfront) pelo
  painel — só administrador, confirmando a própria senha; a senha padrão é
  recusada e a troca fica registrada.

### Corrigido
- Backup do sistema: "Restaurar de outro NewOS (S3)" não listava os
  servidores e backups para escolher.
- Firewall: "Bloquear sempre" era desfeito sozinho após 2 minutos sem
  confirmação; agora a lista de bloqueio vale na hora. Bloquear o próprio IP é
  recusado; IPs já bloqueados aparecem marcados na visão geral; um IP e uma
  rede que o contém na lista não fazem mais o firewall recusar as regras.
- Serviços: o MariaDB não mostra mais o aviso "Referenced but unset
  environment variable" (MYSQLD_OPTS, _WSREP_NEW_CLUSTER).
- Instalador: mensagens de status do systemd não aparecem mais por cima das
  telas (rede, "TPM 2.0 necessário").
- Lint: o JavaScript do painel passa a ser verificado (node --check).
