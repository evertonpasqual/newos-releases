# NewOS 1.6.1


### Correções
- **Prometheus › Importar**: o `snmp.yml` do generator (mais de 1 MiB)
  era recusado com "Part exceeded maximum size of 1024KB" quando colado na
  caixa de texto. A importação agora aceita até 64 MiB por arquivo, colado
  ou enviado, e o teste cobre um `snmp.yml` grande.
