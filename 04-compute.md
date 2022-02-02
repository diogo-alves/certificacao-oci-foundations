# Compute

É o serviço para criação e gerenciamento de instâncias de máquinas na OCI.


## Tipos de instâncias

![tipos de instâncias](https://k21academy.com/wp-content/uploads/2020/06/types-of-instances.png)

### Bare Metal (BM)

Uma instância bare metal tem acesso direto ao hardware físico na infraestrutura da Oracle, o que garante a ela alto desempenho. Esse modelo de instância também possui maior nível de isolamento e controle, pois o hardware é dedicado a um único cliente (modelo single-tenant).


### Virtual Machine (VM)

Criada a partir da virtualização do hardware na OCI, possui um alto grau de escalabilidade. Apesar do hardware ser compartilhado entre diversos clientes (modelo multi-tenant), a virtualização garante um bom nível de isolamento.


### Dedicated Virtual Machine Hosts (DVH)

São instâncias de VMs que rodam em servidores bare metal,
combinando o hardware dedicado com a virtualização gerenciada pela Oracle.


## Processadores Suportados

* Intel
* AMD
* Ampere (Arm)


## Tipos de Shapes

Um shape é um template que determina o número de OCPUs¹, RAM e outros recursos que são alocados para uma instância. A Oracle disponibiliza shapes com configurações que se adequam a diferentes requisitos de aplicações.

*¹ OCPU (Oracle Compute Unit) é a unidade que a Oracle usa para medir processamento.  Cada OCPU equivale a 1 core físico com 2 threads de execução.*


### Standard

Projetados para uso geral, oferecem equilíbrio entre recursos básicos como CPU, memória e rede.


### DenseIO

Projetados para contextos que exigem alto desempenho de armazenamento de dados, como aplicações de big data. Para isso utilizam SSDs NVMe, que garantem maior velocidade de leitura e escrita.


### GPU

Projetados para aplicações que requerem uso de aceleração de hardware (machine learning, por exemplo). Usam CPUs Intel ou AMD e GPUs da NVIDIA.


### High Performance Computing (HPC)

Projetados para atividades que exigem processamento de alto desempenho, como resolução de problemas matemáticos e científicos complexos.


### Otimized

Projetados para contextos que necessitam do alto desempenho dos HPC combinado à baixa latência de rede.


### Flexibles

Permitem a personalização das quantidades de memória e OCPUs alocadas para uma instância, otimizando o uso dos recursos e minimizando os custos.


## Tipos de Capacidades

É possível escolher a capacidade computacional de uma instâncias que melhor se adequa a cada contexto.


### On-Demand

É o tipo padrão, em que se paga apenas pelo que foi usado. A cobrança geralmente é feita com base no tempo de uso da instância, mas pode variar de acordo o shape escolhido (por exemplo: mesmo off, uma instância DenseIO continua utilizando o armazenamento SSD, então faz sentido que esse período continue sendo cobrado).


### Preemptible

Utiliza hardware ocioso que pode ser realocado para outros clientes a qualquer momento, sendo, por isso, até 50% mais barato que o modelo on-demand. É ideal para aplicações que rodam por curto período ou que podem ser interrompidas sem prejuízo.


### Reserved

Reserva capacidade computacional em um AD para ser utilizada no futuro. Pode ser útil em casos de recuperação de falhas, por exemplo, onde é necessário iniciar um novo ambiente rapidamente. Essa reserva antecipada gera um custo, mas dependendo da situação pode até sair mais barata que a opção on-demand.


### Dedicated

Permite que a execução de VMs seja feita em servidores dedicados (único tenant). Este recurso foi disponibilizado com o propósito de atender clientes que legalmente são impedidos de utilizar servidores compartilhados (orgãos governamentais, por exemplo).


## Outras Categorias de Instâncias

### Burstable Instances

São instâncias de VMs que são pouco utilizadas na maioria do tempo (exemplos: microserviços, sites estáticos, CI/CD, etc), mas que ocasionalmente precisam aumentar o nível de performance.

### Shielded Instances

Possuem mecanismos de blindagem do firmware, evitando que softwares maliciosos alterem o boot das máquinas.


## Live Migration

Processo de migração de VMs de um host que precisa de manutenção para um outro host saudável. Todo processo é realizado sem interrupção na execução das instâncias.


## Tipos de Scaling

![tipos de scaling](https://bloggolinux.files.wordpress.com/2020/04/scaling.png)

### Vertical Scaling

Possibilita a alteração do shape da instância, sendo possível aumentar ou diminuir sua capacidade computacional. Esse processo só pode ser feito com arquiteturas de hardware compatíveis e requer da instância um curto período de inatividade até sua conclusão.


### Autoscaling (Horizontal Scaling)

![autoscaling](https://www.viniciusdba.com.br/blog/wp-content/uploads/2020/08/Screen-Shot-2020-08-15-at-15.46.16.png)

O Autoscaling, permite, através de configuração e com base na necessidade da aplicação, adicionar ou remover VMs do *[pool de instâncias](https://docs.oracle.com/pt-br/iaas/Content/Compute/Tasks/creatinginstancepool.htm)* de forma automática. Além da escalabilidade, essa funcionalidade entrega também um alto nível de disponibilidade, pois se uma VM deixa de executar por alguma falha, outra VM é iniciada para substituí-la.


# OS Management

É um serviço gratuito para gerenciamento e monitoramento de atualizações de patches e pacotes do sistema operacional das instâncias.


## Patch Management

Patches são atualizações de software com a finalidade de corrigir bugs, adicionar novas funcionalidades e melhorar a performance e segurança do OS. A função do Patch Management é fazer o gerenciamento desses patches em todas as instâncias, eliminando a necessidade de instalações manuais.


## Package Management

O propósito do package manager é instalar, remover, listar e atualizar de forma centralizada todos os pacotes de software utilizados em um grupo de intâncias Linux.


# Cloud Shell

É um terminal acessível através do console web. O serviço é gratuito e dá direito a um armazenamento de 5GB, além de fornecer um shell Linux com uma CLI pré-autenticada e várias outras ferramentas úteis.

*NOTA: O Cloud Shell funciona com base na região selecionada no console web. Caso seja necessário trocá-la, uma nova instância do serviço deverá ser iniciada. Também é importante estar atento à duração da sessão, que é de, no máximo, 24h, com um timeout de 20 minutos de inatividade.*


## Comandos úteis

### Criar chaves SSH

```shell
ssh-keygen -t rsa
```

### Recuperar chave SSH pública

```shell
cd .ssh
cat *.pub
```