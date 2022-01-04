# es-cluster-docker

if you use docker v2, replace `docker-compose` -> `docker compose`

## 首次启动

```bash
$ docker-compose -f create-certs.yml run --rm create_certs

$ docker-compose -f ./elastic-docker-tls.yml up es01 es02 es03 -d

$ docker exec es01 /bin/bash -c "bin/elasticsearch-setup-passwords auto --batch --url https://es01:9200"

# replace kibana_system's password in kibana.yml

$ docker-compose -f ./elastic-docker-tls.yml up kib01 -d

# open 'https://localhost:5601/' in web browser
```

如果启动失败，可能需要配置系统参数vm.max_map_count：

立即生效，重启失效：

```
sysctl -w vm.max_map_count=262144
```

永久生效，需要重启：

```
vi /etc/sysctl.conf
vm.max_map_count=262144
```


## 后续运行

```bash
docker-compose -f ./elastic-docker-tls.yml up -d
```

if you need certs:

```bash
docker cp es01:/usr/share/elasticsearch/config/certificates/bundle.zip .
```
