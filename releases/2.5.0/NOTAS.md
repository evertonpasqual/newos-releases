# NewOS 2.5.0


### Novo
- **NewOS Manager** (console central da NewFront em
  `newmanager.newfront.cloud`): cada NewOS manda um sinal de vida a cada
  60 s pelo agente `newos-link` (HTTPS, só de saída; funciona atrás de
  qualquer NAT). No Manager aparecem cliente, versão, online/offline e o
  básico de uso. Nada do conteúdo do servidor sai dele.
- **Ativação obrigatória na ISO nova**: depois do login, o painel só libera
  com a **chave de ativação** gerada no Manager (uso único, presa à
  máquina, exige internet) e com a troca da senha padrão do admin. Quem
  tiver a ISO e a senha padrão não passa da tela de ativação.
- Servidores **atualizados** (instalados antes) não travam: entram no
  Manager como **pendentes** e são aprovados lá.
- Servidor revogado no Manager volta a pedir a chave.
- Sistema › Servidor: cartão **NewOS Manager** (estado, cliente, último
  contato, "Verificar agora").
