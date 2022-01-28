# Stack de monitoramento TIG (Telegraf, Influxdb e Grafana)

## Telegraf
Será responsavel por coletar as metricas de acordo com a config do arquivo "telegraf.comf"

## Influxdb
Armazena os dados das metricas coletados pelo telegraf

## Grafana
Onde é mostrado atraves de dashboards as metricas coletadas

### Dashboards dessa stack
Metricas do Docker
Metricas da maquina host
metricas da app que esta no docker

### Adicionar novos dashboard

Novos dashboards podem ser adicionados, colocando o arquivo "json" do dashboard a pasta "gf-dashboard".

Tambem podem ser adicionados atraves do portal oficial:
https://grafana.com/grafana/dashboards
