# NewOS 2.24.0


### Cofre da NewFront (Vaultwarden), pelo NewOS Manager
- **Ativação em 3 passos:** chave, senha gerada (copiar) e **duplo fator obrigatório** (QR code + código). A senha só muda no fim, junto com o duplo fator, e os dois vão para o cofre pelo NewOS Manager (versão 1.21 ou mais nova).
- **No cofre:** um item por servidor na coleção **NewOS-PROXYs**, com o **hostname** do servidor como nome (nunca o padrão "NewOS": enquanto o hostname não for definido, o Manager espera), usuário, senha, o **duplo fator** (o cofre gera os códigos), os IPs como `http://IP:81`, o cliente e a versão. Mudou o hostname ou os IPs, o item acompanha.
- **Sistema › Servidor › Cofre:** mostra se o servidor está no cofre. **Cadastrar no cofre** (servidores que já existem): gera uma senha nova para o admin, liga o duplo fator se ainda não estiver ligado, troca e grava no cofre. A senha nova aparece uma vez, para copiar.
- **Troca segura em duas fases:** o Manager recebe a senha (cifrada) antes, o NewOS troca e confirma, e só então o Manager grava no cofre; se o cofre estiver fora, tenta de novo sozinho. O NewOS nunca guarda credencial do cofre.
- **Recuperação de senha** autorizada no Manager também atualiza a senha no cofre.

### Logs (Graylog): cópia local com limite em GB
- Novo campo **Limite da cópia local (GB)**, padrão **2 GB**. A cópia local serve só para consultar aqui as últimas mensagens (o Graylog guarda tudo). Passou do limite, saem os **dias mais antigos** de todas as fontes; se só o dia de hoje já passar, sai o arquivo de hoje da fonte que mais mandou (o rsyslog recomeça o arquivo). Um equipamento que manda gigabytes por dia não enche mais o `/var`.
- A **fila em disco** (o que ainda não chegou ao Graylog) nunca é tocada.
- A conferência passa de 1 hora para **a cada 10 minutos**. A tela mostra quanto a cópia local está usando.
- Servidor novo vem com **1 dia** de cópia local; os atuais mantêm os dias configurados e passam a respeitar o limite (aplicado já na atualização).
