# NewOS 2.18.5


### Armazenamento: ampliar o disco escolhendo o volume
- **Correção:** depois de aumentar o disco da VM, o "Ampliar" da partição **criptografada** do sistema (NEWOS_CRYPT) só aumentava a partição. O LUKS e o LVM dentro dela continuavam do tamanho antigo, e o espaço novo ficava parado, sem aparecer em nenhum volume. Agora o LUKS e o volume físico LVM crescem junto.
- **Para onde vai o espaço:** o "Ampliar" pergunta qual volume recebe o espaço novo (ex.: VAR, ROOT ou HOME) ou se ele fica livre no grupo para usar depois.
- Partição que já foi ampliada por uma versão anterior, com o espaço parado dentro dela: o "Ampliar" aparece de novo e resolve.

### /var não enche mais com logs
- **Prometheus:** além do prazo (15 dias), o banco ganhou um **tamanho máximo em disco**. O padrão **auto** usa até 30% do /var; passou disso, o mais antigo é apagado antes do prazo. Dá para mudar em Prometheus › Configuração (ex.: 5GB).
- **Logs do NewOS** (`/var/log/newos-*.log`): agora são rotacionados (20 MB ou 1 semana, 4 cópias comprimidas).
- **Journal do sistema:** teto de 1 GB e 1 mês.
- **Módulo Logs:** a cópia local é conferida a cada hora (antes, 1 vez por dia). Com o /var acima de 85%, ela perde os dias mais antigos até voltar a 80%. A fila do que ainda não foi entregue ao Graylog não é tocada.
