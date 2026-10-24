# NewOS 1.9.0


### Novo
- **Instalação pergunta a rede** (ISO nova): para o cliente instalar
  sozinho, antes de apagar o disco o instalador mostra telas para escolher
  a **placa de rede** (com MAC e se o cabo está conectado), **IP fixo ou
  DHCP**, **IP**, **máscara** (255.255.255.0 ou 24), **gateway** e **DNS**,
  com validação (gateway precisa estar na mesma rede) e uma tela final de
  confirmação que mostra o disco que será apagado e o endereço do painel.
  Mais nada é perguntado. Para instalar sem perguntas:
  `NETWORK_ASK="no"` no `newos.conf`, ou o parâmetro de kernel
  `newos.net=conf` / `newos.net=placa:IP/24:gateway`.
- **Proteção do boot (senha do GRUB)**: sem a senha, ninguém no console
  edita o boot (tecla `e`) nem abre o console do GRUB — o caminho para
  trocar a senha de root. O servidor continua ligando sozinho; opções
  avançadas e modo de recuperação pedem a senha (usuário `root`). A ISO já
  instala protegido (`GRUB_PASSWORD` no `newos.conf`); em **Sistema ›
  Servidor** o administrador troca ou remove a senha (confirmando a própria
  senha do painel). Servidores atualizados ficam sem senha até alguém
  defini-la ali.

### Melhorado
- Sair do painel fecha só os terminais abertos **naquele navegador**; os de
  outro navegador da mesma pessoa continuam.

### Corrigido
- Teste do backup do sistema tolera a queda do SSH durante a restauração.
