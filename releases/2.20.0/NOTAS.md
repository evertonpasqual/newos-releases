# NewOS 2.20.0


### Docker
- **Atualizar imagem:** botão em cada container que subiu pelo painel. O NewOS baixa a imagem de novo e, se veio versão nova, recria o container com a mesma configuração (portas, volumes, variáveis, limites). Os dados dos volumes ficam; se a versão nova não subir, o container antigo volta. Dá para forçar a recriação mesmo sem versão nova.
- **Docker › Compose:** projetos com vários containers colando o `docker-compose.yml`. O NewOS confere cada serviço com as mesmas regras do Novo container (sem privileged, rede do host, build, cap_add, dispositivos, socket do Docker ou pasta do sistema; portas livres e fora das do NewOS) e põe os limites de CPU e memória (o do arquivo, até o teto, ou o padrão). Editar, parar, subir, baixar imagens novas, ver os logs e excluir (com ou sem os volumes). Os projetos ficam em `/srv/docker/compose/<projeto>`; `./pasta` no arquivo é dentro do projeto.
- **Avisos por e-mail (Sistema › Notificações, categoria Docker):** container que parou sozinho (não pelo painel), que reinicia sem parar, que ficou sem memória ou com a verificação de saúde falhando, e o Docker parado com o módulo ligado. Quando volta, chega o "Resolvido".
- **Onde o Docker guarda os dados:** em Imagens e ajustes, informe a pasta (ex.: `/dados/docker`, num disco montado em Armazenamento). O NewOS confere se cabe, para os containers, copia tudo, liga o Docker na pasta nova, sobe os containers de novo e, se marcado, apaga a cópia antiga. Se algo falhar, volta para a pasta anterior. A trava de 85% passa a olhar o disco dessa pasta.
- Correção: os avisos de erro das telas do Docker apareciam sem cor.
