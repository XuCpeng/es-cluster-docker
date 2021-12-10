# es-cluster-docker

if you use docker v2, replace `docker-compose` -> `docker compose`

## First Setup

```bash
$ docker-compose -f create-certs.yml run --rm create_certs

$ docker-compose -f ./elastic-docker-tls.yml up es01 es02 es03 -d

$ docker exec es01 /bin/bash -c "bin/elasticsearch-setup-passwords auto --batch --url https://es01:9200"

# replace kibana_system's password in kibana.yml

$ docker-compose -f ./elastic-docker-tls.yml up kib01 -d

# open 'https://localhost:5601/' in web browser
```

## After

```bash
docker-compose -f ./elastic-docker-tls.yml up -d
```

if you need certs:

```bash
docker cp es01:/usr/share/elasticsearch/config/certificates/bundle.zip .
```
