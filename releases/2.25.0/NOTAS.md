# NewOS 2.25.0


### Cofre: uma senha só para o admin, o root e o newfront
- **Ativação** e **Sistema › Servidor › Cadastrar no cofre**: a senha gerada (21 caracteres) passa a valer também para o **root** e o **newfront** (console e SSH), não só para o admin do painel. O item do cofre diz isso (campo **Linux (mesma senha)**, com o NewOS Manager 1.22). Se a troca de alguma conta Linux falhar, a tela avisa qual e onde trocar (Usuários › contas Linux); a do painel e o cofre seguem valendo.
- **Recuperação de senha** autorizada no Manager: a senha nova vale também para o root e o newfront (o NewOS recebe só o hash, como antes; o Debian confere o mesmo hash bcrypt).

### Menu: abrir pelo mouse sem atrapalhar a rolagem
- Os grupos do menu continuam abrindo com o mouse, mas só quando o mouse **para** sobre o título (passar por cima, a caminho de outro item, não abre).
- **Rolando o menu, nada abre nem fecha:** a lista fica parada sob o cursor.
- O grupo aberto pelo mouse fica aberto enquanto o mouse estiver no menu; abrir outro fecha o anterior só se ele estiver abaixo (fechar um de cima puxaria a lista). Ao sair do menu, os grupos abertos de passagem fecham. Clicar no título continua fixando o grupo aberto.
