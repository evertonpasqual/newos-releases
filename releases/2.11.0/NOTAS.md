# NewOS 2.11.0


### Novo
- **Sistema › Agendamentos**: tudo o que roda sozinho no servidor, num lugar só.
  - Timers do systemd, **cron** (serviço, jobs e pastas cron.daily etc.) e o
    **agendador do Bareos** (próximos jobs e os últimos que terminaram).
  - Para cada agendamento: quando roda (em português: "todo dia às 02:30"),
    **próxima execução**, **última vez e se deu certo** (com o código de saída
    quando falha), duração e o journal.
  - Avisos no topo: o que falhou na última vez, timer sem próxima execução,
    cron parado. Linha do tempo animada das próximas 24 horas.
  - **Executar agora**, ligar/desligar (tarefas e agendamentos do NewOS).
  - **Tarefas agendadas** criadas pela tela: nome, comando e quando (todo dia,
    semana, mês, a cada N minutos/horas ou expressão do systemd), com prévia
    das próximas execuções. Rodam como root: só administradores, com a senha
    (e o MFA) de novo, e tudo na auditoria. Se o servidor estava desligado na
    hora, rodam ao ligar.

### Corrigido
- **Verificação diária de atualizações e renovação dos pacotes offline paravam
  depois do primeiro boot** (timer "vencido", sem próxima execução). Agora são
  horários de calendário (04:00 e 03:00, com variação aleatória) e a
  atualização rearma os dois.
- Instaladores dos hosts (node_exporter, rsyslog, Zabbix Agent 2) **não ficam
  mais parados sem dizer nada**: mostram cada etapa, têm limite de tempo em
  tudo, esperam o apt do Proxmox liberar (lock) em vez de travar, registram em
  `/var/log/newos-instalar.log` e mostram as últimas linhas se algo falhar.
- node_exporter/zfs_exporter: parar o serviço antigo com limite (e kill se
  preso, avisando se o processo está em estado D por montagem NFS/CIFS/Ceph);
  espera até 60 s pela porta e explica o motivo se não responder.
- Host que não é Debian 12/13: o instalador avisa em vez de esperar o apt do
  host sem internet.

### Testes
- `scripts/dev/agendamentos-test.sh` (etapa 20/21 do pipeline).
