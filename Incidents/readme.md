# FortiMonitor


## Adição de novas instancias

Quando temos redundância de FGT, ambos vão responder pelo mesmo IP, preferencialmente informando o SN do FGT ativo.
Percebi também que em nosso ambiente por estarem interligados via VPN, ao inserir um FGT como Fabric Root, ele consegue puxar informações de todos os equipamentos.

## Configurações

Dentro de cada FGT a ser monitorado, é necessário que a interface habilitada para Fabric tenha uma regra que permita
o trafego por ela na porta 8013(que estaria já implícita), uma vez liberada a conexão com o monitor será estabelecida.

Apesar de estar liberada em nosso FGT de FOR, estamos tomando timeout e ficando sem a coleta, o que nos deixa 'cegos' quanto ao monitoramento via FortiMonitor.

"We received a timeout while attempting to query the root device over the Fabric tunnel. Please verify downstream access is enabled on all relevant FortiGates, and that the root serial number is entered correctly
Error code: fabeng_408"




## Metrics

As seguintes metrics abaixo optei por deixar para fazer em conjunto com o time/supervisão para ter parâmetros de valores.

- SD-WAN Latency
- SD-WAN Packet Loss
- SD-WAN Packet In
- SD-WAN Packet Out


### Incidente simulado

 No incidente #335560252 forcei o status !=up referente a uma SD-WAN para Cloudflare a partir do ISP_02, onde dessa forma não fica claro a causa raiz dele, sendo então a melhor pratica, acredito, na metric definir:

- down
- disable
- error

Dessa forma o troubleshooting ficaria mais assertivo.

É possivel considerar a analise de performance do host para correlacionar ao incidente se fosse o caso.


JPA
10.83.130.254
FG100FTK23071109,FG100FTK23066975
