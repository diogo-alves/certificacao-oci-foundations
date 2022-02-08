# Security

![security zones](https://docs.oracle.com/en-us/iaas/Content/Resources/Images/security-overview-diagram.png)

Os serviços de segurança no OCI fornecem isolamento, gerenciamento de identidade, autorização, criptografia de dados, detecção de vulnerabilidade, monitoramento e outras funcionalidades.

## Modelo de Segurança Compartilhada da OCI

![](https://www.datocms-assets.com/2885/1617146813-screen-shot-2021-03-30-at-4-26-44-pm.png)

**Responsabilidades do cliente**:
* Dados
* Dispositivos que acessam a OCI
* Gerenciamento de usuários e permissões
* Aplicações
* Controle de rede
* Configuração e atualização do sistema operacional

**Responsabilidades da Oracle**:
* Camada de virtualização
* Hosts físicos
* Rede física
* Datacenter físico


### Casos de Uso

![casos de uso](https://i.imgur.com/uUuB7zR.jpeg)


## Cloud Guard

![cloud guard](https://docs.oracle.com/en-us/iaas/Content/Resources/Images/cloud-guard-overview-diagram.png)

É um serviço que monitora, identifica e implementa automaticamente correções para possíveis vulnerabilidades em recursos (targets) da OCI baseado em regras pré-definidas (recipes). 


## Security Zones

![security zone](https://docs.oracle.com/en-us/iaas/Content/Resources/Images/security-zones-overview-diagram.png)

São espaços vinculados a compartimentos onde não é permitido desabilitar políticas de segurança da OCI ([security zone policies](https://docs.oracle.com/en-us/iaas/security-zone/using/security-zone-policies.htm#security-zone-policies)), nem mesmo se o usuário for o admin do tenancy.

Alguns exemplos de políticas de segurança:
* Os recursos em uma security zone não devem ser acessíveis a partir da internet pública.
* O boot volume de uma instância em uma security zone também deve estar em uma security zone.
* Os recursos em uma security zone devem ter backup regular e automático.
* Os dados em uma security zone não podem ser copiados para um compartimento padrão porque podem ser menos seguros.


## Security Advisor

Serviço que unifica as funcionalidades do Security Zone, Cloud Guard com outros serviços, garantindo que as políticas de segurança da OCI sejam sempre cumpridas.

Serviços suportados:
* Secure Object Storage Buckets
* Secure Virtual Machine Instances
* Secure File Systems
* Secure Block Volumes


## Vulnerability Scanning (VSS)

Serviço projetado para verificar rotineiramente (diária ou semanalmente) por vulnerabilidades em instâncias de compute. O serviço gera relatórios detalhados e atribui às vulnerabilidades níveis de risco. Também é possível realizar esse monitoramento diretamente pelo Cloud Guard. 


## Vault

![vault](https://hiteshgondalia.files.wordpress.com/2021/08/oci-vault-5.png)

É um serviço que permite gerenciar informações sensíveis, como credenciais e chaves criptografadas, controlando quais usuários ou serviços devem ter acesso a elas. Para garantir a inviolabilidade das informações, todas as chaves são armazenadas em hardware security modules (HSM), que possuem certificação FIPS 140-2 nível 3. 

Algoritmos de criptografia suportados:
* AES
* ECDSA
* RSA


## Web Application Firewall (WAF)

![WAF](https://www.oracle.com/a/ocom/img/rc24-waf-oke-architecture.jpg)

Serviço que protege aplicações contra tráfego malicioso e indesejado. Ele possui a capacidade de criar e gerenciar regras para barrar ameaças da internet, como XSS e SQL injection, podendo inclusive limitar acessos com base na origem geográfica da requisição.


## Bastion

![Bastion](https://docs.oracle.com/pt-br/iaas/Content/Bastion/images/bastion-overview-diagram.png)

É um serviço que fornece via SSH acesso público e seguro a recursos (instâncias e DBs, por exemplo) que estão em subnets privadas. Sua integração com o IAM permite controlar quem pode iniciar uma sessão e o que pode ser feito através desse acesso. Também é possível configurar uma lista de IPs específicos com permissão para conexão.