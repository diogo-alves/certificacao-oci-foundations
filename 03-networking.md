# Virtual Cloud Network (VCN)

![VCN](https://enabling-cloud.github.io/oci-learning/resources/vcn-infrastructure.png)

VCN é uma rede virtual privada configurada via software na OCI. Se parece com uma rede tradicional, possuindo regras de firewall e tipos específicos de gateways. Sua abrangência é regional, cobrindo multiplos ADs. A OCI suporta a criação de até 200 VCNs por região.

Seu range de IPs vai de /16 até /30. Para IPs privados a Oracle recomenda seguir a RFC 1918 (10.0.0.0/8, 172.16/12 e 192.168/16).


## Subnets

São subdivisões de uma VCN. Elas podem ser públicas (com IPs públicos e privados) ou privadas (com apenas IPs privados), abrangendo uma região inteira ou um único AD. É possível criar até 300 subnets por VCN.



## Security List

Conjunto de regras de firewall aplicadas a uma subnet inteira. Tipos:

* Stateful - Cria uma regra de saída automática
* Stateless - A regra de saída precisa ser configurada


## Network Security Group

![SL x NSG](https://docs.oracle.com/pt-br/solutions/oci-security-checklist/img/nsg-seclist-png.png)

Semelhante à security list, mas atua num nível mais granular, direto na interface de rede virtual (VNIC) de uma instância (ou load balancer, db, etc).


## Gateways

![Tipos de gateways](https://docs.oracle.com/en-us/iaas/Content/Resources/Images/network_service_gateway.png)


### Internet Gateway

Fornece um caminho para o tráfego de informações entre as instâncias dentro das subnets públicas e a internet. Seu acesso é bidirecional, com as conexões podendo ser originadas tanto da subnet quanto da internet. Uma VCN pode ter apenas um internet gateway.


### NAT Gateway

Esse tipo de gateway permite que instâncias dentro de uma subnet privada tenham acesso à internet. Diferente do internet gateway, seu acesso é unidirecional, ou seja, pode iniciar conexões com a internet e receber respostas, mas não pode receber conexões iniciadas na internet.


### Service Gateway

Um service gateway permite que a VCN acesse de forma privada serviços Oracle específicos de uma região sem expor os dados a um NAT gateway ou à internet. Todo o tráfego da VCN para o serviço em questão é percorrido através da malha da rede Oracle. 


### Dynamic Routing Gateway (DRG)

É um serviço que fornece tráfego privado entre a VCN e outras redes remotas. Através do DRG, é possível conectar via IPSec VPN ou FastConnect ambientes On Premise diretamente com uma VCN na OCI. Para cada VCN haverá apenas um DRG.


## Peering

### Remote Peering Connection (RPC)

![RPC](https://askmedawaa.files.wordpress.com/2020/05/800.png)

É um recurso do DRG que conecta VCNs de regiões diferentes.


### Local Peering Gateway (LPG) 

![LPG](https://blog.hussaindba.com/wp-content/uploads/2019/01/c-users-firozhussain4045-downloads-network_local_.png)

Conecta VCNs de uma mesma região.


## Route Tables

São conjuntos de regras de roteamento que enviam o tráfego para fora da VCN (internet, rede local ou VCN Peering) utilizando gateways. Sempre que uma VCN é criada, uma Default Route Table é gerada automaticamente, sendo utilizada por padrão pelas subnets. O ideal é que cada subnet tenha sua própria route table.


## Opções de conectividade

![connect options](https://docs.oracle.com/pt-br/solutions/oci-security-checklist/img/connectivity-options-png.png)


### Internet

* IPs reservados gratuitos
* IPs efêmeros, atrelados ao recurso enquanto este não for terminado
* Cobrança por tráfego de saída, com 10TB/mês grátis


### IPSec VPN

* Serviço gratuito de VPN da Oracle
* Possibilidade de montar uma VPN própria numa instância Compute


### FastConnect

* Conexão privada, sem precisar passar pela internet 
* Baixa latência de rede
* Alta velocidade de conexão, indo de 1 a 10GBps e sendo garantida por SLA
* Cobrança por tempo de uso de porta, sem limite de tráfego


## Network Visualizer

![network visualizer](https://doyensys.com/blogs/wp-content/uploads/2021/04/oracle-network-visualizer-1024x567.jpg)

Exibe a topologia de redes como diagrama.


## Load Balancer

![Load balancer](https://docs.oracle.com/en-us/iaas/Content/Resources/Images/gsg-lb-allow-traffic.png)

Permite a distribuição automática do tráfego entre as instâncias disponíveis na VCN, otimizando o uso de recursos, facilitando a escalabilidade e assegurando alta disponibilidade. Pode ser público ou privado.


### OCI Load Balancer

Realiza proxy de tráfego para as camadas 4 (TCP) e 7 (HTTP).


### Network Load Balancer

É do tipo non-proxy e trabalha nas camadas 3 (UDP) e 4 (TCP). O serviço gratuito e ideal para ambientes de baixa latência (streaming, voip, etc).


### Tipos de Backends

* Weighted Round Robin - Distribui o tráfego sequencialmente entre as instâncias
* IP Hash - Atrela o tráfego de um determinado cliente a uma instância específica
* Least Connections - Direciona o tráfego à instância com menos conexões ativas