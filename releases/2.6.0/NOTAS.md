# NewOS 2.6.0


### Corrigido
- **Prometheus: "Job com nome repetido: pve"**. Importar um Prometheus com
  vários Proxmox no mesmo job deixava o prometheus.yml com o job repetido.
  Daí em diante nenhuma alteração era aceita (nem remover host) e o Prometheus
  ficava com a configuração antiga. Agora cada Proxmox ganha um job próprio e
  o rótulo `job` continua o original (dashboards e alertas não mudam).
- **Importar de novo o mesmo arquivo** atualiza o que já existe com o mesmo
  nome: hosts, jobs, clusters, Proxmox, jobs extras e linhas do /etc/hosts.
  Antes recusava ou deixava o IP antigo.
- **Tempo limite (scrape_timeout) por job** é importado e pode ser ajustado em
  Jobs e clusters. Antes era perdido, e um exporter lento (ZFS, storage
  grande) aparecia fora do ar por estourar o tempo.
- **Instalar o node_exporter num host sem internet**: o script ficava parado
  tentando o GitHub. Agora baixa os pacotes deste NewOS, com o sha256
  conferido, e só tenta o GitHub se o NewOS não entregar. Toda consulta tem
  tempo limite.

### Novo
- **Remover vários hosts de uma vez** no Prometheus: marque os hosts (ou
  todos os do filtro) e clique em Remover selecionados.
- **Motivo da falha à vista**: o host fora do ar mostra o erro da última
  coleta na própria linha.
- **zfs_exporter**: o script de instalação instala o zfs_exporter (porta
  9134) quando o host tem pool ZFS.
- **Comando de instalação**: usa o endereço com que você abriu o painel e
  mostra os outros IPs do NewOS como alternativa.
