# Service Level Agreement (SLA)

SLA é um contrato entre um fornecedor de serviços e o cliente que especifica os serviços a serem prestados, as responsabilidades das partes, o nível mínimo de qualidade garantido e possíveis compensações caso esse mínimo não seja entregue.

A Oracle oferece [SLAs](https://www.oracle.com/br/cloud/sla/) de ponta a ponta, cobrindo três aspectos principais:

* **Disponibilidade (Data Plane)** - Garante um limite de tempo mínimo de disponibilidade dos serviços.
* **Gerenciamento (Control Plane)** - Possibilita gerenciar, monitorar e modificar recursos da OCI.
* **Performance** - Assegura que os serviços estão entregando a performance esperada.


## Níveis e Definições

Os níveis mínimos de um serviço são medidos em percentuais (sempre acima de 99%) e computados mensalmente, com base em 30 dias.

### Exemplo - Vault

Exemplo de definições SLA do serviço Vault:

* **Disponibilidade**: é definida como qualquer chamada de API que realiza uma operação de criptografia e retorna um status HTTP 2xx.

* **Indisponibilidade**: quando alguma chamada de API não consegue realizar uma operação de criptografia.

* **Percentual de atividade mensal**: 100% - tempo indisponível (% em minutos)

Compensações oferecidas pelo SLA caso o mínimo de disponibilidade não seja atingido:

|Percentual de atividade mensal | Crédito|
|:-----------------------------:|:------:|
|Menor que 99,9%|10%|
|Menor que 99,0%|25%|
|Menor que 95,0%|100%|


#### Cenário A

Cliente teve 10 minutos de indisponibilidade no mês (30 dias). Cálculo do SLA:

```python
>>> minutos_contratados = 43_200  # 60 minutos * 24 horas * 30 dias
>>> minutos_inatividade = 10
>>> minutos_utilizados = minutos_contratados - minutos_inatividade
>>> percentual_atividade_mensal = minutos_utilizados / minutos_contratados * 100
>>> round(percentual_atividade_mensal, 2)
99.98
```
Seguindo a tabela do SLA, como o percentual de atividade mensal (99,98%) foi maior que 99,9%, não houve violação do SLA.

#### Cenário B

Cliente teve 1 hora de indisponibilidade no mês. Cálculo do SLA:

```python
>>> minutos_contratados = 43_200  # 60 minutos * 24 horas * 30 dias
>>> minutos_inatividade = 60
>>> minutos_utilizados = minutos_contratados - minutos_inatividade
>>> percentual_atividade_mensal = minutos_utilizados / minutos_contratados * 100
>>> round(percentual_atividade_mensal, 2)
99.86
```
Como o percentual de atividade mensal (99,86%) foi menor que 99,9% e maior que 99.0%, o cliente poderá receber no mês um crédito de 10% sobre o valor do serviço, pois houve violação do SLA.


## Control Plane e Data Plane

Na OCI Control Plane está relacionado à administração de recursos enquanto o Data Plane está relacionado ao uso desses recursos.

Exemplos:

|Service|Control Plane|Data Plane|
|:-----:|:-----------:|:--------:|
|Object Storage|CreateBucket API|GetBucket API|
|Functions|CreateFunction API|InvokeFunction API| 

Criar um bucket ou uma function são operações ligadas ao Control Plane. Já listar um buckets, acessar seu conteúdo ou invocar uma function são operações de Data Plane.

## Support Center

Espaço onde é possível consultar a documentação dos serviços da OCI e abrir tickets sem se preocupar em descrever detalhes do ambiente, pois as principais informações já são capturadas automaticamente.

### Abrindo Uma Solicitação de Suporte

Considerações:

* Apenas contas pagas podem solicitar suporte
* Usuários da modalidade *Always Free* não são elegíveis a utilizar o serviço de suporte.
* O suporte a contas com *Free Tier* é limitado.

Informações necessárias para registar uma solicitação:
* **CSI** (Customer Support Identifier, um número que identifica o cliente)
* **Tenancy OCID** (código que identifica o tenancy utilizado)
* **Resource OCID** (código que identifica o recurso com problema)
