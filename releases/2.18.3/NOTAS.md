# NewOS 2.18.3


### Prometheus: vCenter/ESXi
- **Correção:** o exportador do VMware dava "Sem coleta: HTTP Error 500" com qualquer vCenter, mesmo com usuário e senha certos. O `vmware_exporter` 0.18.4 (o último, de 2022) quebra com o Twisted 24.7 ou mais novo, que o pip instala hoje. Agora ele é instalado com o Twisted 24.3.0, e a atualização corrige sozinha quem já tem o exportador instalado.
- O "Testar" do vCenter diz a causa real, lida no log do exportador: senha recusada, sem permissão, vCenter inalcançável na 443, nome que não resolve ou erro de certificado.

### Visual
- **Aviso na barra de cima:** ao salvar ou testar, a barra fica verde (ok), vermelha (erro) ou amarela (aviso), com a mensagem e um × para fechar. O verde some sozinho; o erro e o aviso ficam até fechar.
- A página **volta para onde estava** depois de salvar, em vez de pular para o topo.
