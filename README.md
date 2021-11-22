# es-cluster-docker

## First Setup

```bash
$ docker-compose -f create-certs.yml run --rm create_certs

$ docker-compose -f ./elastic-docker-tls.yml up es01 es02 es03 -d

$ docker exec es01 /bin/bash -c "bin/elasticsearch-setup-passwords auto --batch --url https://es01:9200"

# replace the password in kibana.yml

$ docker-compose -f ./elastic-docker-tls.yml up kib01 -d

# open 'https://localhost:5601/' in web browser
```

## After 

```bash
docker-compose -f ./elastic-docker-tls.yml up -d
```
