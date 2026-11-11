# NewOS 2.15.0


### Novo
- **Network › Troubleshooting** (módulo novo, só para administradores, com registro na auditoria):
  - **DNS:** consulta com `dig`, comparando o DNS do servidor com outros;
  - **Ping e rota:** perda e latência, com o MTR mostrando cada salto;
  - **Portas abertas:** portas e serviços de um host (`nmap`);
  - **Descoberta de rede:** IP, MAC, fabricante e nome dos equipamentos de uma faixa, até /20;
  - **Saúde das interfaces:** link, velocidade, duplex, erros e descartes, destacando o que está aumentando agora.
- **Monitoramento › Zabbix › Proxy › Hosts monitorados:** lista os hosts que o Zabbix Server entregou a este proxy, com interfaces e quantidade de itens ativos.
