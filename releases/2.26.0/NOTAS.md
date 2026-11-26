# NewOS 2.26.0


### Debian pelo NewOS Manager
- O agente do Manager passa a informar o Debian deste servidor: pacotes com versão nova (e quantos de segurança), a última busca (apt update), o kernel e se pede reinício. Vai no sinal de vida quando muda (e a cada 30 minutos).
- O Manager (1.23 ou mais nova) pode mandar **buscar atualizações** (apt update), **instalar** (apt upgrade) ou fazer a **atualização completa** (apt dist-upgrade). O NewOS roda pelo mesmo caminho de Sistema › Servidor (em segundo plano, com log), recusa dist-upgrade que removeria pacotes sem a confirmação explícita e devolve o andamento e o resultado ao Manager.
- Sem busca há mais de 1 dia, o agente roda o apt update sozinho (só atualiza a lista; não instala nada), para o Manager mostrar o que há de novo.
