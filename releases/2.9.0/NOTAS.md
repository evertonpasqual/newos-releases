# NewOS 2.9.0


### Novo
- **Instalação nos hosts sem internet**: quando um módulo liga, o NewOS baixa
  (com a internet dele) e **guarda** os pacotes que os hosts do cliente usam,
  e renova uma vez por dia (`newos-pkgrepo`, timer diário). O host só precisa
  alcançar o NewOS na porta do painel.
  - Prometheus: `node_exporter`, `zfs_exporter` (sha256 oficial conferido) e
    `smartmontools`. Comando novo: `bash instalar-node-exporter.sh instalar --configure`.
  - Logs: **`instalar-rsyslog.sh`** instala o rsyslog (o Proxmox 8 não traz) e
    encaminha tudo ao NewOS por TCP com fila em disco (`status`, `testar`, `remover`).
  - Zabbix: **`instalar-zabbix-agent2.sh`** instala o Agent 2 da mesma série do
    Zabbix do NewOS e aponta `Server`/`ServerActive` para ele (`--hostname`, `--metadata`).
  - Pacotes Debian 12 e 13 (Proxmox 8 e 9) num repositório apt servido em
    `/dl/apt/`, com a assinatura oficial (Debian/Zabbix) conferida no NewOS; o host
    instala só o que falta. Cada tela mostra o que está guardado e tem
    "Atualizar agora".
- **Dashboards do Grafana por alvo**: botão **Grafana** em cada host, cluster,
  Proxmox e Ceph (Prometheus › Alvos) baixa a dashboard já presa àquele alvo
  (variáveis fixas e escondidas, título e uid próprios: importar várias não
  sobrescreve). Os modelos genéricos ficam em Jobs e clusters.
- **Dashboard do Ceph** (ceph-mgr) no padrão NOC, filtrando pelo rótulo `ceph_cluster`.
- **Prometheus › SNMP**: os módulos do snmp_exporter pela web.
  - Envio de MIBs do fabricante (avisa as que faltam) e **gerador**
    (`generator.yml` → `gerado.yml`), com as MIBs padrão do net-snmp incluídas.
  - Editor do `personalizado.yml` (e do `importado.yml`), com o oficial e o NewIO
    para consulta; tudo validado pelo snmp_exporter antes de valer.
  - Teste de um módulo num equipamento e **tipos de equipamento novos** (ex.:
    `cisco-ios` = `system,if_mib,cisco_saude`).

### Mudou
- A visão geral do Prometheus não tem mais os botões das dashboards genéricas
  (agora em Alvos, por alvo).
- O cache antigo de pacotes do Prometheus (`/var/lib/newos-prometheus/dl`) vira o
  repositório offline (migrado sozinho).

### Testes
- `scripts/dev/offline-test.sh` (etapa 18/19 do pipeline): hosts Debian 12 e 13
  sem internet instalam rsyslog, Zabbix Agent 2, node_exporter e smartmontools
  pelo NewOS; dashboards por alvo; MIBs Cisco + gerador + tipos + editor.
