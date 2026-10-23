# NewOS 1.6.0


### Novo
- **Prometheus › Alvos › Jobs e clusters**: cadastro de jobs (`job_name` +
  porta + intervalo: node, zfs, nginx…) e de clusters (nome + cliente). Cada
  host escolhe o cluster e os jobs de que participa; o mesmo host pode estar
  no node (9100) e no zfs (9134). Os alvos ganham os rótulos `cluster` e
  `cliente` (hosts, Proxmox, Ceph e SNMP) para filtrar nas dashboards, por
  exemplo `up{cluster="TITANIA"}`. Rótulos externos continuam valendo para
  tudo do Prometheus.
- **Prometheus › Importar**: lê o `prometheus.yml`, o `/etc/hosts`, o
  `pve.yml` e o `snmp.yml` de um Prometheus em funcionamento e mostra o que
  será cadastrado antes de gravar. Jobs simples viram jobs + hosts (clusters
  pelo rótulo ou pelo comentário `# cluster NOME`), jobs do pve-exporter
  viram clusters Proxmox com a credencial de cada um, e o resto (SNMP por
  equipamento, blackbox…) entra igual em jobs extras. Os nomes nas
  dashboards (job e instance) continuam os mesmos.
- **Alertmanager externo** em Configuração (central que recebe os alertas).
- **Prometheus › Alertas › Regras**: pacotes de regras com liga/desliga.
  Além dos pacotes NewIO, importa qualquer arquivo de regras por link, com
  atalhos para o [awesome-prometheus-alerts](https://samber.github.io/awesome-prometheus-alerts/)
  (Proxmox, Ceph, VMware, Linux, ZFS, Prometheus, Blackbox, MySQL, Windows,
  Docker). Cada regra liga/desliga e é ajustável: limite (ex.: 95 → 80, e
  o texto acompanha), expressão, tempo, severidade, título e descrição, com
  "voltar ao original". "Atualizar do link" traz a versão nova do pacote
  sem perder os ajustes. Na importação sai a sujeira das descrições da
  comunidade (`VALUE = …`, `LABELS = map[…]`). Tudo validado pelo promtool.
- **Mensagem do Telegram editável** (template do Alertmanager), validada
  pelo amtool renderizando de verdade, com "voltar ao padrão". O padrão
  agora mostra o cluster e usa o cliente do cluster quando houver.
- "Alertas agora" agrupa o mesmo alerta repetido numa linha (×N).
- Tela de Alvos com resumo animado (alvos coletando, fora do ar, hosts,
  clusters), estado de cada job por host e filtro por cluster.

### Correções
- Envio central (remote_write): mostra "sem resposta" quando o central não
  confirma, em vez de "enviando" com atraso de centenas de milhares de horas.
- Campos de URL e horário sem estilo nos formulários; células de tabela com
  legenda saíam desalinhadas.
- O alerta de host fora do ar vale para qualquer job de node_exporter.
- **Backup › Restaurar**: com o Bareos 25.1.2 (repositório oficial
  "current") a restauração era recusada ("O Director recusou a
  restauracao: failed"), tanto para pasta quanto para baixar em ZIP. A
  seleção de arquivos e o pedido agora vão na mesma sessão do Director. O
  teste passou a conferir que a restauração gera um job novo.
