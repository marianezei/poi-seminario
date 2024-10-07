# poi-seminario

Neste repositório contém arquivos que foram utilizados para subir a aplicação e também ferramentas de monitoramento.

O arquivo ```prometheus-deployment.yaml``` contém algumas as configurações que modificamos, ou seja, não foram configurações padrões da instalação com o Helm.

O arquivo ```values.yaml``` também é um arquivo que modifica algumas configurações padrões. Neste, definimos que será usado NodePort, não será usado volumes e a quantidade de recursos.

### Principais Comandos Utilizados com o Helm:
Adiciona o repositório Helm do Grafana:
``` helm repo add grafana https://grafana.github.io/helm-charts ```
Adiciona o repositório Helm da comunidade Prometheus.
``` helm repo add prometheus-community https://prometheus-community.github.io/helm-charts ```

Instala o Grafana no namespace "monitoring" usando as configurações padrão do Helm:
``` helm install grafana grafana/grafana --namespace monitoring ```

Instala o Prometheus no namespace "monitoring" usando a configuração personalizada do arquivo values.yaml:
``` helm install prometheus prometheus-community/prometheus --namespace monitoring -f values.yaml```

Após tudo instalado, foi verificado qual porta foi alocado para o Grafana e Prometheus através do comando:
``` kubectl get svc  --namespace monitoring ```

As outras configurações foram realizadas diretamente no dashboard do Grafana, onde inserimos o IP referente ao Prometheus, escolhemos o tipo de dashboard e configuramos alguns alertas focados nos recursos das instâncias.


### ID do dashboard utilizado no Grafana:
- ID: 1860

### Links úteis
- Para configurar alertas diretamente no Prometheus:
https://samber.github.io/awesome-prometheus-alerts/rules

- Para conhecer novos tipos de dashboard:
https://grafana.com/grafana/dashboards/

- Para saber mais sobre o blackbox:
https://github.com/prometheus/blackbox_exporter


