# NewOS 2.3.0


### Novo
- **Disco criptografado com TPM** (ISO nova): o LVM do sistema fica dentro de
  um LUKS2 que o próprio servidor destrava no boot pelo TPM 2.0 (Clevis, PCR
  7): ninguém digita senha no dia a dia, e o disco levado para outra máquina
  (ou copiado) não abre. `/boot` e a partição EFI ficam fora (o GRUB lê o
  kernel); a senha padrão da NewFront fica como **chave de recuperação**.
  - **TPM 2.0 é pré-requisito**: sem ele o instalador mostra o que fazer
    (Proxmox: TPM State; VMware: vTPM) e para **antes** de apagar o disco.
  - Se o TPM não destravar (VM levada para outro host, TPM trocado), a tela
    do boot pede a chave de recuperação.
  - **Armazenamento**: um disco somado ao LVM do sistema também entra
    criptografado e preso ao TPM, e destrava junto no boot. O mapa dos discos
    mostra "LVM criptografado (LUKS2 + TPM)".
  - `DISK_ENCRYPTION="tpm2"` no `newos.conf`; `"no"` volta ao disco aberto.
- **Logo novo** da NewFront (horizontal, "Soluções em Cloud e TI") no painel,
  no login, no boot, no GRUB e nos relatórios.
- **Login com corredor de datacenter animado** atrás do cartão: racks dos
  dois lados com os LEDs piscando, a luz do teto e o reflexo no piso, a
  câmera avançando devagar. Desenhado no navegador (sem vídeo), leve, pausa
  com a aba escondida e fica parado para quem usa "reduzir movimento".
