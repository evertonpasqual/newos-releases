# NewOS 2.14.0


### Novo
- **Sistema › Notificações**: avisos deste servidor por e-mail, por uma conta autenticada.
  - **Conta SMTP:** STARTTLS (587), SSL/TLS (465) ou sem criptografia (só rede interna). Certificado verificado por padrão.
  - **Destinatários:** até 20.
  - **Modo:** "só erros e avisos" ou "todas as notificações".
  - **Categorias:** cada uma liga e desliga.
  - **Teste:** botão "Salvar e enviar um e-mail de teste".
- **O que é avisado:**
  - backup do sistema (falhou, não chegou ao S3, concluído);
  - NBackup (coleta falhou, chave do equipamento mudou, S3, configuração alterada);
  - rotinas do Bareos;
  - disco acima dos limites (85% e 95%, ajustáveis);
  - serviço em falha e quando ele volta;
  - atualização (falhou, aplicada, versão nova);
  - segurança (5 logins errados, firewall desfez uma mudança não confirmada, login de administrador);
  - suspensão ou desativação pelo NewOS Manager.
- **E-mail na identidade NewFront:**
  - logo embutido (aparece mesmo sem baixar imagens), faixa azul e verde-água;
  - selo de erro, aviso, concluído ou resolvido;
  - detalhes, log e botão "Abrir no painel";
  - versão em texto puro junto.
- **Sem spam:**
  - o mesmo problema só volta a ser avisado depois de 6 horas, e quando resolve chega um "Resolvido";
  - com o SMTP fora, os avisos ficam na fila e o NewOS tenta de novo a cada 5 minutos, por até 24 horas.
- **Tela:** histórico dos envios e problemas em aberto.

### Segurança
- **Senha do e-mail:** cifrada no servidor, só o root lê, nunca volta para a tela nem vai no e-mail.
- **Backup do sistema:** passa a levar a conta de e-mail.
- **Desativar pelo NewOS Manager:** agora também apaga a conta de e-mail e as credenciais do NBackup (depois de mandar o aviso).
