# NewOS 2.7.0


### Novo
- **Controle remoto pelo NewOS Manager** (precisa do Manager 1.1). As ordens
  chegam na resposta do sinal de vida, então funcionam atrás de qualquer
  NAT/firewall e mesmo sem a VPN do cliente.
  - **Atualizar**: o Manager pede e o NewOS aplica sozinho. Só aceita pacote
    assinado pela NewFront, e o resultado volta para o Manager.
  - **Suspender**: para e desabilita Zabbix, Prometheus e exporters, Bareos,
    Tráfego e o backup do sistema. Guarda o que estava ligado e trava o
    painel com o aviso “Servidor suspenso”. Nada é apagado.
  - **Reativar**: religa exatamente o que estava ligado.
  - **Desativar por completo**: para tudo, apaga as credenciais (Zabbix com
    PSK e banco do proxy, chaves do S3 e senha do backup do sistema, token do
    Manager) e os dados coletados (Prometheus, Bareos), trava o painel em
    “Desativado” e desliga o agente. Volta só reinstalando pela ISO.
  - Pelo SSH, como root: `newos-link suspend` / `newos-link resume`.

### Segurança
- O usuário do painel só pode chamar `newos-link` para ativar e consultar o
  estado. Suspender e desativar vêm só do Manager, pelo agente.
