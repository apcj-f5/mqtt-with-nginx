# Deploying EMQX Cluster with NGINX (OSS) MQTT Load Balancing

This is a quick example to show how to deploy EMQX Cluster with Nginx MQTT Load
Balancing.

For more information like how to configure Nginx, please see EMQX Documentation:
[MQTT Load Balancing](https://docs.emqx.com/en/enterprise/v5.1/deploy/cluster/lb-nginx.html).

## Prerequisites

Log in to [MyF5 Customer Portal](https://account.f5.com/myf5) or
[Request a trial license](https://www.nginx.com/free-trial-request/) and
download your nginx-repo.crt and nginx-repo.key files. Store the nginx-repo.crt
and nginx-repy.key in this directory after download.

## Usage

```bash
docker compose up -d
```

Open <http://localhost:18083> to visit EMQX Dashboard.

## Test

EMQX MQTT TCP

```bash
$ mqttx sub --config ./mqttx_cli_emqx_tcp.json

[2023-8-22] [22:26:21] › …  Connecting using configuration file, host: localhost, port: 1883, topic: t/1
[2023-8-22] [22:26:21] › ✔  Connected
[2023-8-22] [22:26:21] › …  Subscribing to t/1...
[2023-8-22] [22:26:21] › ✔  Subscribed to t/1
```

## Test

### EMQX MQTT TCP

Create 10 clients and subscribe to topic `t/{clientid}` with MQTT.

```bash
mqttx bench sub --config ./mqttx_cli_emqx_tcp.json
```

### EMQX MQTT TLS

Create 10 clients and subscribe to topic `t/{clientid}` with MQTT TLS.

```bash
mqttx bench sub --config ./mqttx_cli_emqx_tls.json
```
