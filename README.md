# docker-configuration-files

Docker & Docker Compose configuration files for popular software (MySQL/PostgreSQL/ClickHouse/MongoDB, Redis/Valkey/Garnet/KeyDB, RustFS, Meilisearch, RabbitMQ/Kafka/NATS, Keycloak/Casdoor, Go, PHP (Nginx/Apache) and other).

## Create and start containers in Background

```sh
cd dirname
docker compose up -d
```

## Start containers

```sh
cd dirname
docker compose start
```

## Stop containers

```sh
cd dirname
docker compose stop
```

## Stop and remove containers

```sh
cd dirname
docker compose down
# or stop and remove containers and volumes
docker compose down --volumes
```
