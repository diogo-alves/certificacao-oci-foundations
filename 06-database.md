# Database

![databases](https://i.imgur.com/vdjmQoO.png)
Serviço que permite criar, escalar e proteger facilmente instâncias do Oracle Database na OCI.


## Oracle DB Systems

![](https://k21academy.com/wp-content/uploads/2018/09/DB-System-On-OCI.png)

O serviço de Database da Oracle suporta vários tipos de DB Systems, que variam em tamanho, performance, preço e formas de gerenciamento.


### Virtual Machine DB System

Utiliza uma única instância de VM, oferecendo a opção de provisionamento rápido através do Logical Volume Manager.

Configurações disponíveis:
* Até 24 OCPUs
* Até 320GB de RAM
* Até 40TB de armazenamento em block volume


### Real Aplication Cluster (RAC)

Utiliza duas instâncias de VM para criação de um cluster com alta disponibilidade, onde cada nó fica em um FD diferente.

Configurações disponíveis:
* Até 48 OCPUs
* Até 6400GB de RAM
* Até 40TB de armazenamento em block volume

*NOTA: Este tipo de RAC com 2 nós suporta apenas a seguinte edição do Oracle Database: Oracle Enterprise Edition - Extreme Performance.*


### Bare Metal DB System

Utiliza máquina bare metal para garantir alta performance.

Configurações disponíveis:
* Até 52 OCPUs
* Até 768GB de RAM
* Até 16TB de armazenamento local em NVMe


## Exadata DB System (```Não cai na prova```)

Utiliza uma combinação de hardware e software numa estrutura especializada e pré-configurada para rodar um Oracle Database com ultra performance.


## Autonomous Database

É um ambiente pré-configurado que utiliza machine learning para automatizar tunning, updates, monitoramento, atualizações de segurança, backups, e outras rotinas, sendo adequado para workloads de processamento de transações (ATP) ou data warehouse (ADW).

### Tipos
* **Shared** - O cliente tem acesso total aos recursos operacionais do banco de dados, mas o gerenciamento e manutenção da infraestrutura ficam sob a responsabilidade da Oracle. 

* **Dedicated** - Dá ao cliente o uso exclusivo ao hardware do Exadata.


## Tipos de Licenciamento

* **License Included** - O valor da licença é incluso no custo do serviço.
* **Bring Your Own License (BYOL)** - O cliente traz pra cloud a licença que utilizava em seu ambiente On-Premise.


# Outros Serviços

A OCI também oferece outras opções de bancos de dados, inclusive open source.


## MySQL Cloud Service

É um serviço totalmente gerenciado, sendo 100% desenvolvido e mantido pelo time MYSQL. Possui alta disponibilidade e extrema performance (400x mais rápido que o MYSQL) nas consultas, graças ao serviço HeatWave.


## NoSQL Cloud Service

É um serviço de banco de dados NoSQL em nuvem, totalmente gerenciado e que suporta o armazenamento de documentos JSON, tipo de dados chave/valor além de dados em colunas (tabelas).

Foi projetado para lidar com grandes quantidades de dados em alta velocidade e baixa latência (de no máximo 1 dígito de milissegundo).