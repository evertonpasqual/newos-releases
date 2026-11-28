# NewOS 2.29.0


### Zabbix e Wazuh pelo NewOS Manager (Manager 1.25)
- O agente do Manager (newos-link) passa a informar a **versão do Zabbix** (repositório oficial, Zabbix Agent e Zabbix Proxy: pacote e se estão rodando) e o **agente Wazuh** (instalado, versão, conectado, manager, grupo, id). Vai quando muda e a cada 10 minutos.
- Ordem nova **trocar a versão do Zabbix** (7.0 LTS, 7.4 ou 8.0 LTS), também em massa pelo Manager: o mesmo caminho da tela Monitoramento › Zabbix (repositório oficial + Agent e Proxy instalados). Roda em segundo plano; o Manager recebe **concluído** só se o repositório ficou na versão pedida e o que estava rodando voltou a rodar, senão **falhou** com o motivo.
- Ordem nova **instalar/ligar o Wazuh**: instala o agente onde falta, religa onde parou e atualiza para a versão padrão (manager e grupo do newos.conf).

### Correção
- Backup pedido pelo Manager: o agente esperava o backup terminar para seguir; backup com mais de 1 minuto estourava o tempo do ciclo. Agora a tarefa sobe em segundo plano e o sinal conta o andamento.
