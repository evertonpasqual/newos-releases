# NewOS 2.18.0


### Visual (identidade NewFront)
- Fonte **Ubuntu** e **Ubuntu Mono** (embutidas: funcionam sem internet), azul `#263C7E` e
  verde-água `#1DAAB2` da identidade NewFront em todo o painel.
- Menu lateral em **vidro** (estilo macOS), com brilho e fundo com luzes suaves; item ativo
  em pílula de vidro.
- **Menu recolhível**: o botão no alto do menu (ou Ctrl+B) deixa só os ícones para sobrar
  espaço para as telas e dashboards. Passar o mouse mostra o nome; os grupos (Network,
  Monitoramento…) abrem numa janelinha ao lado. O navegador lembra a escolha.

### Prometheus › Alvos
- Padrão de nomes NewFront, sempre em maiúsculas: **CLUSTER-CLIENTE**, **PVE-CLIENTE** e
  **CEPH-CLIENTE**. Ao digitar o cliente (ou escolher o cluster), o nome se preenche sozinho.
- Todo NewOS já vem com os jobs **node :9100**, **ceph :9283** e **zfs :9134** (não podem ser
  removidos; os servidores que já existem ganham os que faltam, sem duplicar porta).
- Exemplos das telas sem nomes de clientes.
