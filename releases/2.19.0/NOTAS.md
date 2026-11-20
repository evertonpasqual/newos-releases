# NewOS 2.19.0


### Módulo Docker (novo)
- **Menu Docker › Containers:** painel ao vivo de cada container (estado, há quanto tempo, portas com link, CPU e memória com o limite dele, rede, política de reinício) e do conjunto (CPU e memória contra o teto do Docker, espaço do /var). Iniciar, parar, reiniciar, ver os logs e excluir (com ou sem os volumes, confirmando o nome).
- **Docker › Novo container:** cole o `docker run` que você já usa (ou monte pelo formulário). O NewOS confere antes de subir e mostra o que vai rodar; o botão "Exemplo" traz um comando pronto.
- **Docker › Imagens e ajustes:** espaço do Docker, imagens (em uso ou não), "Apagar imagens sem uso" e os limites.
- **O Docker não derruba o NewOS:**
  - todos os containers juntos ficam num teto de memória e CPU (padrão 60%; o resto é do NewOS);
  - cada container nasce com limite próprio (padrão 1 GB e 1 CPU), sem swap extra, até 1024 processos e sem ganho de privilégio;
  - recusa `--privileged`, rede/PID/IPC do servidor, `--cap-add`, `--device`, `--security-opt`, o socket do Docker e pastas do sistema (pasta do servidor só em `/srv/docker`);
  - recusa as portas do NewOS (SSH, painel, Zabbix, syslog, Prometheus, exporters, banco) e qualquer porta já em uso;
  - logs dos containers com rotação (10 MB × 3); recusa subir container com o /var acima de 85%;
  - rede própria dos containers (padrão 10.254.0.0/16), longe da 172.17.0.0/16 do Docker, que costuma colidir com a rede do cliente;
  - o Docker bloqueia o encaminhamento ao iniciar (quebraria o NewOS roteando ou fazendo NAT): o módulo devolve esse controle ao firewall do NewOS.
- **Portas publicadas** ficam abertas para qualquer origem, também com o Firewall ligado; os containers saem para a internet pelo firewall do NewOS.
- Docker do Debian 13 (docker.io). Desligar o módulo para o Docker; imagens e volumes ficam em /var/lib/docker.
