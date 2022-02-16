# Pricing


## Modelos de Cobrança


### Pay As You Go (PAYG)

Modelo de cobrança mais popular, permite que os clientes paguem apenas pelos recursos provisionados e utilizados.

### Annual Universal Credits

Permite que os clientes adquiram créditos, com validade anual, que podem ser utilizados a qualquer momento, em qualquer região, recebendo por isso descontos mais vantajosos que no modelo PAYG. 

### Monthly Universal Credits

Funciona de forma semelhante à versão anual, também com assinatura de 12 meses, mas exige um gasto mensal mínimo. 


### Bring Your Own License (BYOL)

Permite que os clientes tragam licenças de software utilizadas no ambiente on-premise para a OCI.


## Fatores que impactam o preço¹

* **Tamanho do recurso** - Quanto maior o tamanho/quantidade do recurso, maior o custo.
* **Transferência de dados**² - O que exceder 10TB/mês de saída de dados (ou egress) será cobrado (exceto FastConnect).
* **Tipos de recursos** - Functions são mais baratas que VMs, que têm custo menor que Bare Metal, etc....

*¹ Diferente de outros cloud providers, todas as regiões da OCI possuem o mesmo custo.*
*² O custo por tráfego de saída é **10 vezes menor** na Oracle que em outros providers e não há cobrança por tráfego entre entre ADs.*


## Gerenciamento de Custos

### Budgets

São utilizados para rastrear gastos por compartimento. Também emitem alertas quando o orçamento definido está próximo do limite configurado. 


### Cost Analysis

Ferramenta de visualização que ajuda, através de dashboards, tags e filtros, a entender, rastrear e otimizar os gastos na OCI.


### Limits, Quotas and Usage

Permite acompanhar os limites de recursos disponíveis na OCI para o tenancy.


### Compartment Quotas

Serviço que aumenta o controle sobre o consumo de recursos por compartments, permitindo restringir ou desabilitar serviços conforme a necessidade.


## Tagging

![tags](https://docs.oracle.com/en-us/iaas/Content/Resources/Images/tag_defined.png)

Adiciona metadados aos recursos através da  definição de chaves e valores. É possível usar as tags para organizar recursos por contexto (por projeto, centro de custo, etc), controlar seus custos e limitar seus acessos.


### Namespaces

![](https://k21academy.com/wp-content/uploads/2020/01/defined-tags-2.png)

São containers para agrupar tags. Devem ser únicos por tenancy. 