# Arquitetura OCI

![OCI architecture](https://i.imgur.com/GsskYXR.png)


## Regions

São áreas geográficas que possuem um ou mais datacenters (Availability Domains).

Ao escolher uma região:
* Busque a mais próxima dos usuários que utilizarão seu serviço, pois isso garante menor latência e maior performance.
* Verifique se há alguma restrição legal do país sobre o local de armazenamento de dados.
* Fique ciente que novos serviços cloud podem não ser disponibilizados em determinadas regiões, pois isso depende de alguns fatores como demanda, disponibilidade de recursos, legislação local, etc.


## Availability Domains (AD)

É como são chamados os datacenters localizados em uma determinada região. Suas principais características são:

* Isolamento físico¹
* Alta tolerância a falhas
* Baixa latência
* Alta largura de banda
* Criptografia nas conexões com outros ADs

¹ *Os ADs ficam em prédios separados por uma distância segura e não compartilham recursos entre si (rede ou energia elétrica, por exemplo). Isso garante que caso haja algum desastre (enchente, terremoto, etc) nas proximidades de um AD, os outros não serão afetados.*


## Fault Domains (FD)

São conjuntos isolados de hardware e infraestrutura que compõem uma AD (atualmente cada AD possui 3 FD). Visando aplicações que requerem alta disponibilidade, eles adicionam mais uma camada de tolerância a falhas, permitindo que cada instância possa ser replicada em um hardware físico diferente, diminuindo assim riscos de paradas em decorrência de falha  nos equipamentos, quedas de energia e manutenções programadas.


## Tenancy

Equivalente a uma conta com recursos. Por padrão ele já é provisionado com um compartimento root (uma forma de organizar recursos por contextos). 

*DICA: Por questões de segurança, é uma boa prática criar admins e grupos específicos para cada tipo de serviço a ser utilizado, reservando o admin do tenancy apenas ao gerenciamento destes. Também é ideal que sua autenticação use multi fatores (MFA).*


## Compartiments

É uma forma de agrupar, isolar e controlar o uso de recursos relacionados (como rede, instâncias, storage e outros), limitando seu acesso a um grupo de usuários conforme políticas de acesso (policies) definidas pelo administrador.

É comum definir compartimentos para recursos específicos (storage e network, por exemplo), projetos, ambientes (dev, test, prod), equipes, setores, filiais, etc. Inclusive é possível criar subcompartimentos (máximo de 6 subníveis), gerar relatórios de gastos individuais e até criar alertas para quando algum dos compartimentos ultrapassar o orçamento previsto (budgets).

Compartimentos são flexíveis a ponto de permitir que recursos de diferentes regiões sejam agrupados juntos. Eles também são capazes de interagir com outros compartimentos, o que torna possível mover os recursos de um compartimento para outro.
