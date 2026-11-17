# NewOS 2.18.2


### Logs
- **Vários hosts atrás do mesmo IP (NAT)** agora aparecem separados em "Quem está mandando". Antes, 3 hosts que saíam pelo mesmo IP público apareciam como uma linha só, com o nome do último que mandou. A cópia local passa a ficar por IP e nome do host, e "Ver" e "Remover" valem para cada host.
- O nome do host vem da mensagem e nunca sai da pasta (nome forjado com "/" ou ".." é neutralizado).
- O que vai para o Graylog não mudou: cada mensagem já levava o nome do host.
- Pastas recebidas antes da 2.18.2 aparecem como "(antigo)" até expirarem.
