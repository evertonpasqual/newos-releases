# NewOS 1.5.1


### Correções
- **Prometheus › Alvos**: o `instance` dos hosts agora sai como
  `nome:porta` (ex.: `NEWLAB01-PVE:9100`), o formato das dashboards de
  node_exporter no Grafana. Antes saía só o nome, e a dashboard que filtra
  por `nome:9100` não encontrava o host. A configuração é regerada sozinha
  ao atualizar (no modo manual o `prometheus.yml` não é tocado).
- **Sistema › Servidor**: o `/etc/hosts` não podia ser salvo quando havia
  uma linha antiga com o nome do próprio servidor num IP anterior (arquivo
  do instalador ou servidor que mudou de IP). Essa linha agora é tratada
  como do sistema e regerada com o IP atual.
