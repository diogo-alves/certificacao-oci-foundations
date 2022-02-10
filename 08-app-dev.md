# Developer Services


## Resource Manager (ORM)

![](https://www.oracle.com/a/ocom/img/rc36-devops-lightbox-deploy-apps-to-staging-and-production-r1.png)

É um serviço que permite automatizar o provisionamento de recursos na OCI (instâncias, VCNs, load balancers, etc) usando arquivos de configuração do Terraform (.tf ou .tf.json).

Exemplo¹ de configuração para provisionar recursos de rede:

```hcl
# network.tf
resource "oci_core_vcn" "_" {
  compartment_id = local.compartment_iresource "oci_core_vcn" "_" {
  compartment_id = local.compartment_id
  cidr_block     = "10.0.0.0/16"
}

resource "oci_core_internet_gateway" "_" {
  compartment_id = local.compartment_id
  vcn_id         = oci_core_vcn._.id
}

resource "oci_core_default_route_table" "_" {
  manage_default_resource_id = oci_core_vcn._.default_route_table_id
  route_rules {
    destination       = "0.0.0.0/0"
    destination_type  = "CIDR_BLOCK"
    network_entity_id = oci_core_internet_gateway._.id
  }
}

resource "oci_core_default_security_list" "_" {
  manage_default_resource_id = oci_core_vcn._.default_security_list_id
  ingress_security_rules {
    protocol = "all"
    source   = "0.0.0.0/0"
  }
  egress_security_rules {
    protocol    = "all"
    destination = "0.0.0.0/0"
  }
}

resource "oci_core_subnet" "_" {
  compartment_id    = local.compartment_id
  cidr_block        = "10.0.0.0/24"
  vcn_id            = oci_core_vcn._.id
  route_table_id    = oci_core_default_route_table._.id
  security_list_ids = [oci_core_default_security_list._.id]
}
resource "oci_core_internet_gateway" "_" {
  compartment_id = local.compartment_id
  vcn_id         = oci_core_vcn._.id
}

resource "oci_core_default_route_table" "_" {
  manage_default_resource_id = oci_core_vcn._.default_route_table_id
  route_rules {
    destination       = "0.0.0.0/0"
    destination_type  = "CIDR_BLOCK"
    network_entity_id = oci_core_internet_gateway._.id
  }
}

resource "oci_core_default_security_list" "_" {
  manage_default_resource_id = oci_core_vcn._.default_security_list_id
  ingress_security_rules {
    protocol = "all"
    source   = "0.0.0.0/0"
  }
  egress_security_rules {
    protocol    = "all"
    destination = "0.0.0.0/0"
  }
}

resource "oci_core_subnet" "_" {
  compartment_id    = local.compartment_id
  cidr_block        = "10.0.0.0/24"
  vcn_id            = oci_core_vcn._.id
  route_table_id    = oci_core_default_route_table._.id
  security_list_ids = [oci_core_default_security_list._.id]
}
```

¹ *Exemplo tirado do sensacional [projeto](https://github.com/jpetazzo/ampernetacle) do [Jérôme Petazzoni](https://github.com/jpetazzo), que permite criar um cluster Kubernetes na OCI usando o free tier*.



### Workflow do Resource Manager

![workflow](https://docs.oracle.com/en-us/iaas/Content/Resources/Images/rmWorkflow.png)

A imagem acima representa uma visão geral do workflow do Resource Manager, com destaque para a Stack, que é a coleção de todos os recursos que estão sendo provisionados pela configuração do Terraform. 


## Functions

Serviço sob demanda que possibilita executar aplicações sem precisar se preocupar com provisionamento e escalonamento de recursos. É um ambiente serveless baseado no projeto open source *[Fn Project](https://fnproject.io/)*, permitindo que todo o código de aplicação seja isolado em um container Docker. 

Suporta:
* Go
* Java
* Node JS
* Python
* Ruby
* C# (suporte da comunidade)


## Container Engine for Kubernetes (OKE)

É um orquestrador de containers que usa Kubernetes para automatizar o deploy, escalonamento e gerenciamento de containers em clusters. O serviço é gratuito e totalmente integrado com outros serviços, como o IAM.


## Container Registry (OCIR)

É um registry Docker gerenciado pela Oracle onde é possível armazenar, administrar e compartilhar imagens Docker. Aceita repositórios públicos e privados e é completamente integrado a outros serviços da OCI, como IAM, Functions e OKE.


## API Gateway

![api gateway](https://i.imgur.com/lEDijWg.png)

Serviço que permite expor endpoints de APIs privadas na internet. Com ele é possível processar o tráfego de clientes de APIs através de um único endpoint e roteá-lo para vários serviços de backend (como load balancers, instâncias, Functions).

O API Gateway suporta validação de API, transformação de request e response, CORS, autenticação e autorização (através do IAM) e limitação de request.