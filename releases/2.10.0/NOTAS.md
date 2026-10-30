# NewOS 2.10.0


### Novo
- **Sistema › Processos** (módulo novo, em Sistema › Módulos): o monitor de
  processos do NewOS no navegador, no estilo do btop.
  - Ao vivo (1, 2 ou 5 s): CPU total e **cada núcleo**, memória (programas,
    cache, livre), disco (leitura/gravação) e rede, com gráficos.
  - Lista de processos com CPU, memória, **leitura e gravação de disco por
    segundo**, o **serviço** (systemd) e o usuário de cada um; filtro (tecla
    `/`), ordenar por qualquer coluna, **agrupar por serviço**, threads do
    kernel opcionais. As linhas reordenam animadas.
  - Clique numa linha: detalhes (comando completo, há quanto tempo roda,
    threads) e **Encerrar (SIGTERM)**, **Matar (kill -9)** ou **Reiniciar o
    serviço**, sempre com confirmação, só para administradores e na
    auditoria. PID reaproveitado é recusado; o painel, nginx, banco, journald,
    dbus, logind e sshd ficam protegidos.
  - Link direto: `/sistema/processos?q=nginx` (filtro) e `?abrir=PID`.

### Mudou
- **Sem swap: memória toda em RAM.** A ISO não cria mais o volume de swap.
  Nos servidores já instalados, a atualização desliga a swap (só se a RAM livre
  comportar o que estiver nela), tira do fstab, refaz o initramfs sem
  hibernação e **devolve o volume ao /var** (4 GB a mais).
- **Sem o balão de memória do hipervisor** (`virtio_balloon` bloqueado): a VM
  fica sempre com toda a RAM configurada no Proxmox. Com o balão ligado, o
  Proxmox tirava memória da VM quando o host apertava (a VM via 1 GB de 8) e
  aí entrava a swap. Recomendado também desligar o *Ballooning Device* na VM.

### Testes
- `scripts/dev/processos-test.sh` (etapa 19/20 do pipeline) e `vm-test.sh`
  confere ROOT/VAR/HOME sem SWAP e sem balão.
