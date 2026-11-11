# NewOS 2.16.0


### Novo
- **Network › Troubleshooting**, segunda leva:
  - **Loop na rede:** envia um quadro de teste e vê se ele volta pela própria interface. Também mede broadcasts por segundo, quadros repetidos e mudanças de topologia do STP (TCN), e mostra quem mais manda broadcast;
  - **DHCP e IP duplicado:** lista todos os servidores DHCP que respondem, sem aceitar oferta (acha DHCP não autorizado), e confere por ARP se um IP está duplicado, livre ou em uso;
  - **Vizinhos LLDP/CDP:** switch, porta, VLAN nativa e IP de gerência de onde o servidor está ligado;
  - **Captura de pacotes:** `tcpdump` com filtro, até 20 MB, com resumo na tela e `.pcap` para baixar e abrir no Wireshark;
  - **MTU do caminho:** maior pacote que chega sem fragmentar, apontando quando o ICMP está bloqueado no caminho (buraco negro de MTU);
  - **HTTP/TLS:** código HTTP, tempos de DNS, conexão, TLS e primeira resposta, cabeçalhos e certificado (confiável ou não, dias até vencer, nomes);
  - **SNMP:** teste v2c ou v3 com nome, descrição, uptime e interfaces do equipamento. A community e as senhas não ficam gravadas nem aparecem na saída.
