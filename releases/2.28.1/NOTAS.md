# NewOS 2.28.1


### Wazuh: manager pelo nome
- O agente Wazuh passa a apontar para **wazuh.newfront.cloud**. A 2.28.0 instalava com o IP do manager.
- A atualização corrige sozinha os servidores que já tinham instalado o agente: troca o endereço no `ossec.conf` e reinicia o `wazuh-agent`. Também ajusta o `WAZUH_MANAGER` do `newos.conf`.
