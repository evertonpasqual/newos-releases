# NewOS 2.1.0


### Novo
- **Dashboard: IP de saída.** Abaixo de "Atualizado", discreto: por qual IP
  público este servidor navega (consulta ao ifconfig.me a cada 10 min, com
  reservas), com botão de copiar.
- **Prometheus: "Monitorar um host novo"** em 3 passos na tela do
  Prometheus: o comando pronto para colar no host (baixa o
  `instalar-node-exporter.sh` direto deste NewOS, sem login), o cadastro em
  Alvos e as **dashboards do Grafana prontas para importar**:
  - *NewOS · Host (node_exporter)* e *NewOS · Proxmox VE (pve-exporter)*,
    formato do Grafana 12;
  - usam o Prometheus padrão do Grafana (sem mapear fonte de dados) e têm os
    filtros **cliente › cluster › job › host** com os rótulos que o NewOS põe
    nos alvos; a do Proxmox não vem mais presa a um cluster de cliente.
- **Zabbix Proxy otimizado** já na instalação: Server padrão
  `mon.newfront.cloud`, perfil para ~50 hosts e VMware (pollers, pingers,
  coletores VMware, caches, fila híbrida em memória e 24 h de fila se o Server
  cair), validado pelo próprio `zabbix_proxy -T`. Campos de desempenho na tela
  do Proxy e o botão **Aplicar o perfil otimizado**. Ajustes feitos depois
  são preservados.

### Corrigido
- **Zabbix: trocar a versão antes de ligar o Agent e o Proxy** dava "O script
  action.sh do modulo falhou". Agora a versão é escolhida primeiro e os
  componentes já instalam nela.
