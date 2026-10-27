# NewOS 2.2.0


### Novo
- **Backup do sistema já nasce no S3 central** (ISO nova): agendamento diário
  ligado e destino S3 da NewFront, cada servidor numa pasta com o seu nome na
  raiz do bucket, guardando 30 cópias. As chaves do S3 ficam fora do git
  (`configs/newos.local.conf`) e só entram na ISO, nunca no pacote de
  atualização público. Servidores atualizados não mudam.
- **Restaurar de outro NewOS (S3)** em Sistema › Backup e restauração: conecta
  no bucket (o configurado ou um informado na hora, sem salvar), lista os
  servidores (uma pasta cada, com quantidade, data e versão do último backup),
  busca pelo nome, mostra os backups do servidor escolhido e restaura com um
  clique. Feito para o NewOS recém-instalado que vai substituir um antigo.
- **Serviços: log ao vivo**, no estilo do Tráfego ao vivo: o journal dos
  serviços a cada 2 s, mais novas em cima com destaque, filtro por serviço,
  por gravidade (tudo / avisos e erros / só erros) e por texto, contadores de
  avisos e erros, pausar; botão de log em cada serviço da tabela.
- **Prometheus já aponta para a central**: remote_write
  `http://45.6.116.215:8428/api/v1/write` e Alertmanager externo
  `45.6.116.215:9093` vêm preenchidos ao ligar o Prometheus pela primeira vez
  (mudam em Configuração).

### Melhorado
- A lista "Cópias guardadas" mostra só os backups **deste** servidor no S3 (os
  dos outros ficam em "Restaurar de outro NewOS").
- Senha padrão da NewFront (ISO): os backups já saem **cifrados** e o GRUB
  já vem protegido com ela. Fica no `configs/newos.local.conf`, fora do git.

### Corrigido
- Leitura do `newos.conf` pelos helpers: vale a última ocorrência de cada
  chave (como no shell) e aceita valores entre aspas simples.
