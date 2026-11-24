# NewOS 2.22.0


### Recuperar a senha pelo NewOS Manager
- No login, embaixo do "Entrar", um link discreto **Esqueci a senha**. A pessoa informa o usuário e o código do app autenticador (a recuperação exige a verificação em duas etapas ligada na conta).
- Com o código certo, o NewOS pede ao **NewOS Manager** (versão 1.20 ou mais nova). Lá, **só um administrador** autoriza ou recusa. Ao autorizar, o Manager gera a senha nova (21 caracteres, mesmo padrão do cofre) e mostra **só para quem autorizou**. O NewOS recebe apenas o hash da senha, grava e confirma; a senha nunca aparece na tela do NewOS.
- A tela do NewOS acompanha sozinha: aguardando, senha trocada, recusado ou expirado (o pedido vale 15 minutos). Se a tela for fechada, o agente aplica a troca no ciclo seguinte do mesmo jeito.
- Código errado conta como tentativa de login errada (bloqueia depois de várias); o mesmo código não vale duas vezes. Tudo fica na auditoria do NewOS e do Manager.
- Servidor sem ligação com o Manager (ou suspenso) não oferece a recuperação.
