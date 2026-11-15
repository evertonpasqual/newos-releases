# NewOS 2.17.1


### Dashboards do Grafana (botão Grafana em Monitoramento › Prometheus › Alvos)
- **Ceph** usa a nova tela de TV da NewFront: saúde, alertas traduzidos, OSDs por host,
  capacidade, PGs/recuperação e desempenho. Sai presa ao Ceph cadastrado (nome exato) e com
  o cliente no banner.
- **Host (node_exporter)** e **Proxmox** com a nova identidade visual e reorganizados para
  TV 1920×1080. A primeira tela mostra o que pede ação: no host, estado, alertas, serviços com
  falha, saúde do sistema (OOM, disco só leitura, RAID, ZFS, inodes, NTP) e partições; no
  Proxmox, VMs/CTs paradas, CPU/RAM/storage, nós, uso por storage, guests e os top 10. Os
  gráficos de histórico ficam abaixo.
- Proxmox **com replicação ZFS cadastrada** (campo "Nós para a replicação ZFS") ganha a faixa
  de replicação na primeira tela (jobs, OK, atrasadas, com falha, desativadas) e, logo abaixo, os
  jobs com origem → destino e a duração. Sem replicação cadastrada, o bloco não aparece.

### Correção
- Servidor revogado no Manager: o aviso "Este servidor foi revogado" na tela de ativação
  sumia no ciclo seguinte do newos-link (virava "aguardando chave"). Agora fica até a chave nova.
- Os painéis da tela de TV usam os plugins `marcusolsson-dynamictext-panel` e
  `gapit-htmlgraphics-panel` no Grafana.
