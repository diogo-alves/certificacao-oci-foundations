# Storage

![](https://k21academy.com/wp-content/uploads/2018/08/storage-option-in-OCI.png
)
A OCI possui diversas opções de armazenamento de dados.

## Local NVMe

Esse tipo de armazenamento usa SSDs NVMe diretamente acoplados a máquinas bare metal, o que garante altas taxas de transferência e IOPS. É indicado para aplicações que precisam de alto desempenho durante a manipulação de dados.


## Block Volume

É um serviço de storage que oferece alta capacidade de armazenamento persistente e conexão via rede. Um Block Volume pode ser provisionado dinamicamente. Ele também é bem flexível em cenários de migrações, podendo ser acoplado a uma instância e remanejado para outra sem que haja perda de dados.

Existem dois tipos de volumes:

* **Block volume** - bloco que permite expandir dinamicamente a capacidade de armazenamento de uma instância
* **Boot volume** - bloco removível que contém a imagem usada para inicializar uma instância de Compute


## File Storage

Serviço que possibilita o compartilhamento de arquivos em rede de forma escalável, durável e com alta disponibilidade. Suporta os protocolos NFSv3 e NLM.


## Object Storage

Serviço para armazenamento de objetos (arquivos de qualquer tipo, com tamanhos individuais de até 10TB), que podem ser acessados via internet. Os objetos são armazenados em *buckets*, que possuem opções para controle de acesso e versionamento dos arquivos.

O serviço oferece duas camadas de dados:

* **Standard** - Para dados que são acessados com frequência.
* **Archive** - Para dados que raramente são acessados, mas que precisam ser preservados por longos períodos (backups, por exemplo).


# Migração de Dados


## Data Transfer Disk

É um serviço de migração de dados offline que permite mover grandes quantidades de dados de um datacenter para o serviço de Object Storage da OCI. Para a migração ser realizada é necessário que o cliente envie os dados para a Oracle em HDs. Até o momento este serviço está disponível apenas nas regiões ```us-phoenix-1```, ```us-ashburn-1``` e ```eu-frankfurt-1```.


## Data Transfer Appliance

Semelhante ao Data Transfer Disk, este serviço utiliza um [hardware específico](https://www.youtube.com/watch?v=Zo-pPV_s5LI&ab_channel=OracleLearning), alugado da Oracle, para o envio dos dados e realização da migração. Até o momento ele está disponível apenas nos Estados Unidos e na União Européia.


## Storage Gateway

![Storage Gateway](https://k21academy.com/wp-content/uploads/2020/01/123-1.png)

O Serviço Storage Gateway é um gateway de armazenamento na nuvem que, por meio de protocolos NFSv4, permite conectar aplicativos locais aos buckets do Object Storage.
