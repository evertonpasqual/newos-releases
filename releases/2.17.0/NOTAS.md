# NewOS 2.17.0


### Console e SSH
- Tela do console nova: logo da NewFront, NewOS e a versão, endereço do painel e o aviso de **acesso restrito** ao time NewFront. O mesmo aviso aparece antes do login por SSH.
- Depois do login: resumo do servidor (cliente e situação no NewOS Manager, IPs, painel, uso, módulos).
- **Logout automático**: console e SSH parados por 10 minutos encerram a sessão (`CONSOLE_TIMEOUT`). O Terminal do painel fica de fora.

### NewOS Manager
- O sinal de vida leva o resumo dos backups (backup do sistema e equipamentos do NBackup), sem senha nem chave: o Manager 1.8 mostra se está em dia e baixa as cópias direto do S3.
