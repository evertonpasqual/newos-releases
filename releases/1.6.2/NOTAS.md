# NewOS 1.6.2


### Correções
- **Prometheus › Equipamentos SNMP**: só havia uma community v2c (e um
  usuário v3) para todos os equipamentos; um switch com outra community
  (ex.: `NEWFRONT`) não era descoberto e a tela mostrava só "HTTP Error
  500". Agora há **várias credenciais com nome** (v2c ou v3), cada
  equipamento usa a sua, e na descoberta dá para digitar a community na
  hora: ela vira credencial (ou reaproveita a que já tem a mesma). As
  credenciais do `snmp.yml` importado também aparecem para escolher.
- A descoberta mostra o motivo real quando o equipamento não responde
  ("sem resposta com a credencial X: confira community, SNMP ligado, UDP
  161") em vez do erro HTTP do snmp_exporter.
- Cada equipamento SNMP pode ter nome, tipo, credencial e cluster
  alterados depois.
