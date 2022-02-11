# Observability & Management


## Monitoring

![monitoring](https://docs.oracle.com/en-us/iaas/Content/Resources/Images/monitoringOverview.png)

Serviço que permite monitorar, através de métricas e alarmes, recursos utilizados na OCI.

### Métricas

![métricas](https://docs.oracle.com/pt-br/solutions/oci-gpu-monitoring/img/metrics_explorer.png)

São dados que ajudam a monitorar a integridade, capacidade e performance dos recursos em uso.


### Alarmes

![alarms](https://docs.oracle.com/en-us/iaas/Content/Resources/Images/alarms-topic-diagram.png)

Funcionalidade responsável por alertar os administradores sempre que as métricas indicarem determinado nível de uso de um recurso (uso excessivo de CPU, por exemplo).


## Logging

Serviço que fornece acesso a logs de recursos da OCI de forma centralizada. Esses logs incluem informações críticas de diagnóstico que descrevem o desempenho e o acesso dos recursos.

Tipos de logs:
* **Audit logs** - Emitidos pelo serviço OCI Audit.
* **Service Logs** - Emitidos por serviços nativos do OCI (API Gateway, Events, Functions, Load Balancers, etc).
* **Custom Logs** - Emitidos por apps personalizados, outros cloud providers ou ambientes on-premises.


## Logging Analytics

É um serviço baseado em machine learning que monitora, agrega, indexa e analisa todos os dados de log de aplicações que rodam em ambientes on-premises e multicloud. Com ele é possível pesquisar, explorar e correlacionar esses dados para solucionar e resolver problemas mais rapidamente e derivar insights para tomar melhores decisões operacionais.