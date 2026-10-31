# NewOS 2.12.0


### Novo
- **Firewall › Grupos** (como os aliases do pfSense): dê nome a endereços
  (ex.: `GRUPO-SEDE`) ou a portas e use nas regras. Viram conjuntos do
  nftables: editou o grupo, todas as regras que o usam mudam juntas.
  - Endereços: IP, rede e os atalhos `@redes-locais` (as redes das placas
    deste NewOS, atualiza sozinho), `@redes-privadas`, `@qualquer`, `@zona:lan`.
  - Portas: `443`, `udp/161`, `tcp+udp/53`, `tcp/9100-9102`.
  - Grupo em uso não sai; cada cartão mostra quem usa.
- **Mapa do firewall** (Visão geral): origens (grupos, zonas, internet) →
  escudo do NewOS → serviços, com o tráfego **ao vivo**: partículas fluem nas
  regras que liberam (na velocidade dos pacotes reais) e batem no escudo no que
  é bloqueado. Passe o mouse para destacar um fluxo.
- **Regras com grupos**: origem por grupo(s) e serviço por grupo de portas,
  além de zona, endereços e portas soltas.
- **Cada serviço liberado ganha o seu grupo**: as portas em uso ao ligar o
  firewall e as dos módulos (ex.: `SYSLOG` do módulo Logs). Liberar mais IPs =
  editar o grupo.

### Mudou
- **Painel (porta 81) pelo grupo `PAINEL-ADMIN`**: num firewall novo ele nasce
  com as redes das interfaces deste NewOS + `45.6.119.253/32` e
  `177.44.202.10/32` (NewFront) + o IP de quem estava usando o painel ao ligar
  (ninguém fica trancado para fora). O NewOS recusa tirar do grupo o IP de
  quem está editando.
- **SSH nasce bloqueado** (o console fica no Terminal do painel); liberar para
  um ou mais grupos em Firewall › Proteção › Painel e SSH.
- Servidores com o firewall já ligado **não mudam sozinhos** (o painel e o SSH
  continuam como estavam); a tela mostra o botão **Aplicar o padrão NewFront**.
- Quem está no `PAINEL-ADMIN` continua entrando no painel mesmo com bloqueio
  por país.

- **Clonar regra** (Firewall › Regras): o formulário abre com tudo da regra
  original; a cópia entra logo abaixo dela.
- **Agendamentos**: a tabela do cron não quebra mais (comando longo termina em
  "…"); o cartão do Bareos só aparece com o módulo Backup ligado; horários do
  cron traduzidos ("todo dia 1 do mês às 06:52", "a cada 10 min", "a cada 2 h").

### Testes
- `firewall-test.sh`: SSH bloqueado ao ligar, PAINEL-ADMIN padrão, grupos
  (conjuntos no nftables, edição, em uso, trava do próprio IP), padrão
  NewFront, clonar regra. `logs-test.sh`: regra do Syslog pelo grupo SYSLOG.
  `prometheus-test.sh`: espera a 1a coleta SNMP (job a cada 60 s).
