# NewOS 1.5.0


### Novo
- **Sistema › Servidor**: troca do hostname e do domínio pelo painel, com
  prévia do nome completo (FQDN). Atualiza `hostnamectl`, `/etc/hostname`,
  `/etc/mailname`, as linhas do próprio servidor no `/etc/hosts` e a
  configuração do NewOS. Opcional: sincronizar o novo nome no Zabbix Agent
  e no alvo local do Prometheus.
- **Editor do `/etc/hosts`**: entradas do administrador (IP, nomes,
  comentário) numa tabela; as linhas do sistema (localhost, IPv6 e o
  próprio servidor) são mantidas automaticamente. Valida IPs e nomes,
  recusa o mesmo nome em dois IPs e guarda a cópia anterior em
  `/etc/hosts.newos-bak`.
- Helper `newos-system` e teste `scripts/dev/system-test.sh`
  (20 verificações), incluído no pipeline como etapa 11.
- **Sistema › Backup e restauração**: backup do próprio NewOS num pacote
  único (nome e `/etc/hosts`, rede, montagens e pools ZFS, módulos e
  componentes ligados com a configuração de cada um, catálogo do Bareos,
  usuários e ajustes do painel, chaves do SSH). Pode ser protegido por
  senha (AES-256), baixado pelo navegador e restaurado neste servidor ou
  num NewOS recém-instalado. Antes de restaurar, a tela confere versão,
  integridade (sha256) e o que existe aqui (placas de rede, discos pelo
  UUID) e deixa escolher cada parte. Os módulos são reinstalados e a
  configuração volta por cima; as sessões do painel caem no fim.
- **Agendamento** do backup do sistema (diário ou semanal) com retenção,
  para uma pasta num disco montado e/ou um bucket S3 (AWS, MinIO, Ceph,
  Wasabi; assinatura v4 sem dependências), com botão de teste do bucket.
  Último resultado exposto ao Prometheus (`newos_sysbackup_last_status`).
- Helper `newos-sysbackup`, unidades `newos-sysbackup.{service,timer}` e
  teste `scripts/dev/sysbackup-test.sh` (S3 real via versitygw, download,
  servidor "estragado" e restaurado pelo painel), etapa 12 do pipeline.
