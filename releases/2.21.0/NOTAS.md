# NewOS 2.21.0


### Menu novo
- **Visual novo do menu lateral:** painel em vidro azul NewFront com ícones isométricos (no mesmo padrão do NewOS Manager, com desenhos próprios do NewOS). O item da página atual é uma aba clara que se junta ao conteúdo e desliza até o item clicado.
- **Busca no menu:** campo no alto do menu (atalho **Ctrl+K**, ou ⌘K no Mac). Filtra itens e subitens enquanto você digita; Enter abre o primeiro, Esc limpa.
- **Disco /var no pé do menu:** anel com o uso do /var (amarelo a partir de 80%, vermelho a partir de 90%), com atalho para Armazenamento.
- **Menu recolhido:** vira um trilho de ícones redondos; os grupos abrem numa janela ao lado e a lista rola quando não cabe na tela.

### Primeiro acesso
- Depois da chave de ativação, a senha padrão do admin é trocada por uma **senha gerada pelo NewOS**: 21 caracteres com letras maiúsculas e minúsculas, ao menos 3 números e 3 especiais (`!@#$%^&*`). Não dá para digitar outra: a tela só mostra a senha para copiar (ou gerar outra) e pede a confirmação "Copiei e guardei".

### Prometheus
- Servidor novo já vem com **"Guardar dados por: 5d"** e a interface web em **"Só este servidor"** (os dados seguem para o central pelo remote_write). Servidores já configurados ficam como estão.
