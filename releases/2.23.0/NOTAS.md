# NewOS 2.23.0


### Sistema › Servidor: atualizações do Debian e energia
- **Atualizações do Debian:** mostra quantos pacotes têm versão nova (e quantos são de segurança), quando foi a última busca e se o servidor pede reinício. Botões **Buscar atualizações** (`apt update`), **Instalar atualizações** (`apt upgrade`) e **Atualização completa** (`apt dist-upgrade`).
- Antes de instalar, a tela mostra o que vai ser atualizado, instalado e removido. Se a atualização completa for remover algum pacote, só começa marcando a confirmação.
- Roda sem perguntas, mantendo os arquivos de configuração atuais, numa tarefa própria do sistema: continua mesmo se o painel reiniciar no meio. A tela acompanha o log ao vivo; o log fica em `/var/log/newos-os/apt.log`. Uma tarefa por vez.
- **Energia:** **Reiniciar** e **Desligar** o servidor pela tela, com a senha do painel. Desligar avisa que só volta pela máquina (hipervisor, console). Ao reiniciar, a tela espera o servidor voltar e leva ao login. Não deixa reiniciar no meio de uma atualização.
- Só administradores. Tudo vai para a auditoria.

### Menu
- O item da página atual ficou mais discreto: vidro um pouco mais claro, contorno fino e uma barra verde-água acesa à esquerda (no lugar da aba branca). Continua deslizando até o item clicado.
- Menu recolhido: sem o botão de busca (Ctrl+K abre o menu já na busca). O item atual vira um círculo com contorno verde-água em vez de branco.
