# Stack de observabilidade TIG (Telegraf, Influxdb e Grafana)

Nessa stack de observabilidade contemplei o TIG para monitorar host onde ela é implantada, os logs dos containers (Docker), juntos com alguns `stats` da app e um painel docker com quantidade de imagens, containers criados, rodando e parados.

## Rodando a stack

Ajuste os **environments** do `compose file` e do `influxv2.env`.

Algumas estão default, mas a `DOCKER_INFLUXDB_INIT_ADMIN_TOKEN` terá que gerar um token aleatorio e alterar nos arquivos citados.

```bash
docker-compose up -d
```
### Removendo

```bash
docker-compose down -v --rmi local
```

## Telegraf
Será responsavel por coletar as metricas de acordo com a `config` do arquivo `telegraf.conf`.

## Influxdb V2
Armazena os dados das metricas coletados pelo telegraf.

### Acessando Influxdb V2 dashboard
> http://localhost:8086/signin

Login e senha definidos no serviço `influxdb_cli` no `compose file`.

## Grafana
Onde é mostrado atraves de dashboards as metricas coletadas.

### Dashboards dessa stack
Metricas do Docker
Metricas do telegraf v1 e v2
Metricas da app

### Adicionar novos dashboard

Novos dashboards podem ser adicionados, colocando o arquivo "json" do dashboard a pasta "gf-dashboard".

Tambem podem ser adicionados atraves do portal oficial:

>https://grafana.com/grafana/dashboards

### Acessando Grafana dashboard
>http://localhost:3000/

Login: admin
Senha definida no serviço `grafana` no `compose file`.

#### Referencias
 - https://github.com/InfluxCommunity/InfluxDBv2_Telegraf_Docker
 - https://github.com/influxdata/influxdata-docker
 - https://hub.docker.com/_/influxdb/
 - https://hub.docker.com/r/grafana/grafana/
 - https://grafana.com/docs/grafana/latest/installation/docker/
 - https://grafana.com/docs/grafana/latest/administration/provisioning/
 - https://grafana.com/docs/grafana/latest/datasources/influxdb/provision-influxdb/
 - https://docs.influxdata.com/influxdb/v2.1/#
 - https://docs.influxdata.com/influxdb/v2.0/install/?t=CLI+Setup
 - https://docs.influxdata.com/influxdb/v2.0/tools/grafana/
 - https://docs.influxdata.com/influxdb/v2.0/tools/grafana/?t=InfluxQL
