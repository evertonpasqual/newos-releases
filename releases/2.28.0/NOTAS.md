# NewOS 2.28.0


### Logs: equipamento em outro fuso aparece na hora certa no Graylog
- O syslog comum (RFC 3164) não diz o fuso. Um equipamento em outro fuso, ou com o relógio errado, chegava ao Graylog horas antes ou depois e sumia da busca "últimos minutos". Foi o caso dos Proxmox do cliente MPRR.
- Agora, se a hora da mensagem difere **mais de 5 minutos** da hora em que o NewOS recebeu, ela vai com a **hora de recebimento**. A hora escrita pelo equipamento fica em `_hora_origem` e a diferença, em segundos, em `_diferenca_s`. Com diferença pequena, vale a hora do equipamento, como antes.
- Vale para todos os equipamentos sem mexer no fuso de nenhum. A atualização reaplica o envio sozinha onde o módulo Logs está ligado.

### Sistema › Servidor organizado em abas
- Abas **Atualizações e energia** (Debian, reiniciar/desligar, hora certa), **Segurança** (NewOS Manager, cofre, Wazuh, senha do GRUB) e **Identidade e /etc/hosts**.
- Os cartões do topo resumem o servidor (nome e FQDN, Manager, cofre, Wazuh) e levam direto ao cartão. Endereços antigos (`#cofre`, `#grub`, `#hosts`...) abrem a aba certa.

### Agente Wazuh instalado sozinho ao cadastrar no cofre
- Quando o servidor é **cadastrado no cofre** (na ativação ou em Cadastrar no cofre), o NewOS instala o **agente Wazuh 4.14.7** em segundo plano, apontando para o manager da NewFront no grupo `NEWOS`. Se o agente já existir, não mexe.
- A instalação segue os passos oficiais: instala `lsb-release`, `sudo` e `curl` se faltarem, baixa o pacote de packages.wazuh.com, instala com `WAZUH_MANAGER` e `WAZUH_AGENT_GROUP`, depois `daemon-reload`, `enable` e `start` do `wazuh-agent`. O log fica em `/var/log/newos-os/wazuh.log`.
- O cartão **Segurança › Wazuh** mostra se o agente está **conectado ao manager**, a versão, o manager, o grupo, o ID do agente e o último contato. Agente parado ou sem conexão aparece em destaque, com **Tentar de novo** e **Instalar e ligar de novo**.
- Manager, grupo e versão ficam no `newos.conf` (`WAZUH_MANAGER`, `WAZUH_AGENT_GROUP`, `WAZUH_AGENT_VERSION`). Servidores antigos usam o mesmo padrão. Com `WAZUH_MANAGER=""` não instala, como nas VMs de teste.
