# Identity and Access Management (IAM)

O IAM permite criar e controlar usuários, grupos e políticas de acesso (policies) a compartimentos e recursos específicos.

![IAM](https://docs.oracle.com/pt-br/solutions/oci-security-checklist/img/iam-model-png.png)

## Users

São identidades persistentes configuradas através do IAM para representar pessoas ou aplicações.


## Groups

São coleções de usuários que possuem o mesmo tipo de acesso aos recursos.


## Policies

São permissões de acesso a recursos da OCI. São declaradas com a seguinte sintaxe:
```
Allow group <group_name> to <verb> <resource-type> in tenancy
Allow group <group_name> to <verb> <resource-type> in compartment <compartment_name> [where <conditions>]
```
Exemplos de uso:
```
Allow group XYZ to inspect compartments in tenancy
Allow group Administrators to manage all-resources in tenancy
Allow group api-group to use virtual-network-family in compartment project
Allow group SaoPaulo-Admins to manage all-resources in tenancy where request.region='gru'

```

### Verbos

| Verbo | Tipos de Acesso | Usuários-Alvo |
|:-----:|-----------------|--------------|
|`inspect`|Lista recursos, mas sem acesso a informações|Auditores internos|
|`read`|`inspect` + metadados do usuário/recurso|Auditores de terceiros
|`use`|`read` + ações que variam com o tipo de recurso|Usuários finais de recursos|
|`manage`|Inclui todas as permissões|Administradores|      

### Tipos de recursos

|Agregador de recursos|Tipos de recursos|
|:-------------:|------------------|
|`all-resources`|Todos os recursos|
|`database-family`|db-systems, db-nodes, db-homes, databases|
|`instance-family`|instances, instance-images, volume-attachments|
|`object-family`|buckets objects|
|`virtual-network-family`|VCN, subnet, route-tables, security-list, dhcp-options, etc|
|`volume-family`|volumes, volume-attachments, volume-backups|

## Credenciais

Há vários tipos de [credenciais](https://docs.oracle.com/pt-br/iaas/Content/Identity/Concepts/usercredentials.htm) gerenciadas pelo IAM. As utilizadas para acesso à OCI são:

* User e password - Acesso via console web
* API signing keys (não confundir com as chaves SSH de instâncias) - Acesso via CLI/SDK
* Auth tokens (não expiram) - Acesso via APIs de terceiros