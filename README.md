# Stack de observabilidade TIG (Telegraf, Influxdb e Grafana)

Nessa stack de observabilidade contemplei o TIG para monitorar host onde ela é implantada, os logs dos containers (Docker), juntos com alguns `stats` da app e um painel docker com quantidade de imagens, containers criados, rodando e parados.

## Rodando a stack

### Configurando os _environments_

São três arquivos que precisam ser alterados [influxv2.env](influxv2.env), [ds.yml](gf-provisioning/datasources/ds.yml) e o proprio [compose file](docker-compose.yml).

Lista do que precisa ser definido:

- DOCKER_INFLUXDB_INIT_USERNAME=[YOUR USER HERE]
- DOCKER_INFLUXDB_INIT_PASSWORD=[YOUR PASSWD HERE]
- DOCKER_INFLUXDB_INIT_ORG=[YOUR ORG HERE]
- DOCKER_INFLUXDB_INIT_BUCKET=[YOUR BUCKET HERE]
- DOCKER_INFLUXDB_INIT_ADMIN_TOKEN=[YOUR TOKEN HERE]
- DOCKER_INFLUXDB_INIT_DBV1=[YOUR DB HERE]
- DOCKER_INFLUXDB_INIT_RPV1=[YOUR RP HERE]

>É somente procurar o "[YOUR ... HERE]" e alterar conforme variavel.

### Executando

```bash
docker-compose up -d
```
### Removendo

```bash
docker-compose down -v --rmi local
```

## Telegraf
Será responsavel por coletar as metricas de acordo com a `config` do arquivo [telegraf.conf](telegraf.conf).

## Influxdb V2
Armazena os dados das metricas coletados pelo telegraf.

### Acessando Influxdb V2 dashboard
> http://localhost:8086/signin

Login e senha definidos no serviço `influxdb_cli` no [compose file](docker-compose.yml).

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
Senha definida no serviço `grafana` no [compose file](docker-compose.yml).

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
