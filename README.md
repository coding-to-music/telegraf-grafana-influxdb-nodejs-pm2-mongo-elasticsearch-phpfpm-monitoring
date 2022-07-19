# telegraf-grafana-influxdb-nodejs-pm2-mongo-elasticsearch-phpfpm-monitoring

# 🚀 YYYYYYY 🚀

https://github.com/coding-to-music/telegraf-grafana-influxdb-nodejs-pm2-mongo-elasticsearch-phpfpm-monitoring

From / By https://github.com/ZaharBozhok

https://github.com/ZaharBozhok/telegraf-grafana-influxdb-nodejs-pm2-mongo-elasticsearch-phpfpm-monitoring

## Environment variables:

```java

```

## GitHub

```java
git init
git add .
git remote remove origin
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:coding-to-music/telegraf-grafana-influxdb-nodejs-pm2-mongo-elasticsearch-phpfpm-monitoring.git
git push -u origin main
```

## Learning TIG stack on different technologies

#### Monitoring stack:

- telegraf
- grafana
- influxdb
- influxdb_v2

#### Stack to be monitored:

- mongo
- nginx
- phpfpm
- elasticsearch
- nodejs + pm2

### ℹ️ How to make telegraf with influxdb_v2

For learning purpouse created monitoring panels for pm2 using flux which is supported only by influxdb_v2

So in order to make telegraf work with inflxudb_v2 you have to generate token for telegraf in influxdb_v2 admin panel and create bucket named 'telegraf', then insert token in telegraf/env.telegraf

### ℹ️ How to make grafana work with influxdb_v2

In order to make grafana work with influxdb_v2 you have to go to datasources and configure token there also, you can use admin's for learning purpose

### ℹ️ Importing already created dashboard for all this stuff

Import on grafana admin panel dashboard and just paste whole grafana/dashboard.json

### 🤢 "Fixing" nginx strange behvior

Nginx shoulnd't work untill you change nginx ip address in telegraf/telegraf.conf, I specified ip of my local network cause when accessing it via docker network nginx responses with internal server error ¯\\\_(ツ)\_/¯.

### 🌐 Reference repositories and links

[Laradock](http://laradock.io/http:// "Laradock")

[Docker-influxdb-grafana](https://github.com/nicolargo/docker-influxdb-grafana)

[PM2 + grafana + influxdb](https://medium.com/@nikunjd.np/pm2-microservices-monitoring-with-grafana-influxdb-54fb6f8b5d2d)

```
phpfpm_1         | 192.168.0.10 -  19/Jul/2022:05:48:20 +0000 "GET /status" 200

elasticsearch_1  | {"@timestamp":"2022-07-19T05:48:20.013Z", "log.level": "WARN", "message":"received plaintext http traffic on an https channel, closing connection Netty4HttpChannel{localAddress=/192.168.0.4:9200, remoteAddress=/192.168.0.10:49476}", "ecs.version": "1.2.0","service.name":"ES_ECS","event.dataset":"elasticsearch.server","process.thread.name":"elasticsearch[64019cd4ef11][transport_worker][T#1]","log.logger":"org.elasticsearch.xpack.security.transport.netty4.SecurityNetty4HttpServerTransport","elasticsearch.cluster.uuid":"ttqnD76gSaGXUAfwV3IwPw","elasticsearch.node.id":"vaye9bU_QmyzByuaXEAWDw","elasticsearch.node.name":"64019cd4ef11","elasticsearch.cluster.name":"docker-cluster"}

influxdb_v2_1    | ts=2022-07-19T05:48:11.118444Z lvl=info msg=Unauthorized log_id=0bmFloW0000 error="authorization not found"

influxdb_1       | [httpd] browser_ip_address - - [19/Jul/2022:05:48:11 +0000] "POST /write?consistency=any&db=telegraf HTTP/1.1 " 204 0 "-" "Telegraf/1.23.2 Go/1.18.3" 5f86a8a9-0726-11ed-800c-0242c0a80007 3194

telegraf_1       | 2022-07-19T05:48:11Z E! [outputs.influxdb_v2] When writing to [http://influxdb_v2:8086]: failed to write metric to telegraf (401 Unauthorized): unauthorized: unauthorized access
telegraf_1       | 2022-07-19T05:48:11Z E! [agent] Error writing to outputs.influxdb_v2: failed to send metrics to any configured server(s)

telegraf_1       | 2022-07-19T05:48:20Z E! [inputs.docker] Error in plugin: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/info": dial unix /var/run/docker.sock: connect: permission denied
telegraf_1       | 2022-07-19T05:48:20Z E! [inputs.docker] Error in plugin: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/json?filters=%7B%22status%22%3A%7B%22running%22%3Atrue%7D%7D&limit=0": dial unix /var/run/docker.sock: connect: permission denied

telegraf_1       | 2022-07-19T05:48:20Z E! [inputs.nginx] Error in plugin: error making HTTP request to ip_address/status: Get "server_ip_address/status": unsupported protocol scheme ""

telegraf_1       | 2022-07-19T05:48:20Z E! [inputs.elasticsearch] Error in plugin: Get "http://elasticsearch:9200/_nodes/_local/stats": EOF
```