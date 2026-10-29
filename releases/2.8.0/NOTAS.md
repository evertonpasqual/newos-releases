# NewOS 2.8.0


### Novo
- **Módulo Logs (Graylog)**: o NewOS passa a ser o concentrador de syslog da
  rede do cliente, como o Zabbix Proxy é para as métricas (precisa do NewOS
  Manager 1.2). Passo a passo completo em `docs/logs-graylog.md`.
  - **Recebe** syslog em UDP e TCP 514 de servidores Linux e Windows (NXLog),
    VMware ESXi, Proxmox, firewalls, switches e roteadores.
  - **Envia ao Graylog central** por GELF/TCP com TLS mútuo. Cada mensagem
    leva `cliente`, `newos`, `origem_ip`, `origem`, `app` e `facility`.
  - **Certificado deste NewOS** emitido pelo Manager: a chave nasce aqui e não
    sai, vale 30 dias e é renovado sozinho. O Graylog só aceita certificados
    da CA do Manager.
  - **Fila em disco** (padrão 5 GB): internet ou Graylog fora do ar, nada se
    perde, e tudo é enviado quando voltar.
  - **Tela Monitoramento › Logs**:
    - estado, mensagens recebidas, enviadas e na fila, e o erro do rsyslog
      quando não consegue enviar;
    - "Enviar mensagem de teste", que também testa o TLS;
    - quem está mandando, com as últimas linhas de cada fonte (cópia local
      de alguns dias);
    - os comandos prontos, com o IP do NewOS, para cada tipo de equipamento.
  - Com o Firewall ligado, a porta é liberada **só para redes internas**.
  - **Suspenso pelo Manager**: para de receber e de enviar, e volta sozinho
    ao reativar. Desativado por completo: certificado, fila e cópia local
    são apagados.

### Melhorado
- Firewall: os módulos podem ter regras próprias, que saem quando o módulo é
  desligado. Editar uma delas mantém o dono.
- ISO: `rsyslog-gnutls` incluído.
