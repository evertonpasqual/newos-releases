# NewOS 2.0.0


### Novo
- **Módulo Benchmark** (Ferramentas › Benchmark): mede o desempenho real do
  servidor e gera um **relatório na identidade NewOS** para apresentar à
  diretoria (resumo executivo, classificação, gráficos, resultados, ambiente,
  campo de parecer técnico editável, assinaturas, imprimir/PDF e "salvar com
  parecer").
  - **Disco (fio)**: escolha onde testar — sistema de arquivos (arquivo
    temporário), pool ZFS (volume temporário, como o disco de uma VM) ou disco
    vazio (teste direto, com confirmação). Perfil **rápido** (os comandos de
    referência: gravação e leitura sequencial 1 MB, fila 32, `--fsync=10000`)
    ou **completo** (baseline: sequencial, aleatório 4K fila 64 × 4 jobs, misto
    70/30 e latência). Tamanho e tempo ajustáveis; o arquivo de teste é apagado
    ao final, mesmo se interrompido.
  - **Rede (iperf3)**: este servidor como **servidor** (liga/desliga, porta,
    libera a porta no Firewall só enquanto ligado, lista os testes recebidos)
    ou como **cliente** (IP, porta, `-P` 1/4/10/20/outro, envio, recebimento
    `-R` ou os dois `--bidir`, TCP ou UDP com banda alvo).
  - **Internet**: download, upload, latência e jitter com vários fluxos, pela
    Cloudflare (ponto mais próximo) ou pelo Speedtest.net, com velocímetros.
  - Tudo ao vivo: etapas, números animados e gráfico enquanto o teste roda;
    histórico com relatórios guardados no servidor; um teste por vez.
- **Módulo Tráfego ao vivo** (Configurações › Network › Tráfego ao vivo):
  banda de cada interface com gráfico de 60 s e uso do link, quem (IP) está
  falando com o servidor e quanto (entrando, saindo, passando), serviços por
  porta e as maiores conexões, atualizando a cada 2 s (conntrack com contagem
  de bytes). Botão **Abrir o iptraf-ng**, que roda o iptraf-ng no navegador
  pelo terminal do painel (só administradores, com a senha de novo).

### Melhorado
- Menu: módulos podem acrescentar itens dentro de grupos fixos (Network).
- Terminal do painel abre aplicativos de tela cheia de uma lista fixa
  (iptraf-ng), além do shell.
