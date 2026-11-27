# NewOS 2.27.0


### NBackup: pfSense
- Fabricante novo **pfSense** (CE e Plus): a coleta entra pela interface web (HTTPS) com um usuário que só precisa do privilégio **WebCfg - Diagnostics: Backup & Restore** e baixa o **config.xml completo** (sem os gráficos RRD), como o roteiro oficial do pfSense. Versões, diferenças, S3 e alertas iguais aos outros equipamentos; o certificado da WebGUI é fixado no primeiro acesso.
- **Para recuperar:** instale um pfSense novo e use Diagnostics › Backup & Restore › Restore Backup com o arquivo baixado (a versão do pfSense sai como **.xml**). O passo a passo do usuário somente leitura está no cadastro.

### Prometheus › Alvos: editar vários hosts de uma vez
- Selecione os hosts e use **Editar selecionados**: troque o **cluster** e escolha os **jobs** (deixar exatamente estes, acrescentar ou tirar), para todos de uma vez. Ex.: crie o CLUSTER-TESTE, marque os hosts, escolha o cluster e marque node, zfs e ceph. Nenhum host fica sem job; o promtool confere antes de valer.

### Backup pedido pelo NewOS Manager
- O Manager (1.24 ou mais nova) pode mandar fazer **agora** o backup do sistema (gera e envia aos destinos configurados) ou a coleta do NBackup. Roda em segundo plano, numa unidade própria, e o andamento e o resultado (nome e tamanho do pacote, ou o erro) voltam ao Manager. No histórico do backup, a origem aparece como "pedido pelo Manager".

### Dashboard
- Ícones isométricos animados e discretos nos cartões de processador, memória, disco e rede.
