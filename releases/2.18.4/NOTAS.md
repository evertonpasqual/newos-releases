# NewOS 2.18.4


### Prometheus: dashboard do vCenter pronta
- **Botão Grafana no vCenter** (Monitoramento › Prometheus › Alvos › vCenter / ESXi): baixa a tela de TV do VMware já presa àquele vCenter, como as de Host, Proxmox e Ceph. É só importar no Grafana.
- A tela filtra pelo **vCenter cadastrado** (o rótulo `instance`, ex.: vCenter-JVE). O filtro **Cluster vSphere** fica dentro dele: em **All** mostra o vCenter inteiro (todos os clusters, hosts, VMs e datastores); escolhendo um cluster, só ele.
- Modelo genérico com o filtro de vCenter: link **VMware** em Alvos, ao lado de hosts, Proxmox e Ceph.
