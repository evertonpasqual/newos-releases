# NewOS 1.4.0


### Atualizações automáticas
- **Sistema › Atualizações**: o NewOS verifica uma vez por dia (e em
  "Verificar agora") se há versão nova no repositório público de releases
  `github.com/evertonpasqual/newos-releases` (o código continua privado).
  Faixa "NewOS X disponível" no topo e ponto no menu; a tela mostra o que
  muda em cada versão e atualiza com um clique (confirmação digitando a
  versão), acompanhando o progresso ao vivo — o painel reinicia no fim e a
  tela continua sozinha.
- **Pacote assinado**: cada versão tem SHA256SUMS assinado (ed25519) pela
  chave da NewFront; o NewOS recusa pacote sem assinatura válida ou com
  checksum diferente. A chave pública vai dentro do NewOS; a privada fica
  só na máquina de quem publica.
- Aplica pelo mesmo `update-panel.sh` do deploy: preserva a configuração,
  guarda a versão anterior e volta sozinho se falhar. Versão MAIOR não é
  aplicada (exige a ISO).
- `scripts/release-publish.sh`: publica a versão da tag (git archive),
  assina e atualiza o `latest.json` com as notas do CHANGELOG.
