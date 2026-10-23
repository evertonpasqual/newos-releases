# NewOS 1.7.0


### Novo
- **Módulo Firewall** (nftables, opcional, menu **Firewall**). Zonas = as
  funções das interfaces em Network (WAN, LAN, DMZ, Gerência).
  - **Visão geral**: estado, atividade **ao vivo** (o que foi bloqueado ou
    liberado e por quê), quem mais foi bloqueado (com "bloquear sempre"),
    zonas e as **portas abertas deste servidor** com quem pode chegar nelas.
  - **Regras** de entrada (acesso a este servidor) e de encaminhamento
    (entre redes): liberar/bloquear/recusar por zona, endereço, protocolo e
    porta, com atalhos de serviços, ordem, liga/desliga, registro opcional e
    contador de pacotes ao vivo.
  - **NAT**: a LAN sai pela WAN (masquerade) e redirecionamento de portas
    (porta da WAN → IP:porta interno, origem opcional).
  - **Proteção**: quem administra (painel/SSH de qualquer lugar ou só de
    zonas/endereços confiáveis), bloqueio automático de força bruta e de
    varredura de portas (expira sozinho), SYN flood, ping com limite,
    pacotes inválidos, lista de bloqueio.
  - Ao ligar, o que já estava em uso continua liberado. Painel e SSH nunca
    ficam atrás das suas regras. **Toda alteração volta sozinha em 2
    minutos** se não for confirmada (faixa no topo, como na rede). O
    nftables valida antes de aplicar; nada muda se recusar.
- **Verificação em duas etapas (MFA)** no painel, por usuário (Minha
  conta): QR code para qualquer app autenticador (Google/Microsoft
  Authenticator, Authy…), 8 códigos de recuperação de uso único, o mesmo
  código não vale duas vezes. Contas mostra quem usa MFA e o administrador
  pode desativar o de quem perdeu o celular.
- **Hora certa com chrony** usando sempre a.ntp.br, b.ntp.br, c.ntp.br,
  d.ntp.br e ntp.usp.br (sem o pool do Debian), na ISO e nos servidores
  atualizados. Sistema › Servidor mostra a sincronização e cada servidor.
