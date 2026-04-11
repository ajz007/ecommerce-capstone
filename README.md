# Capstone Ecommerce Backend

This repository contains a three-service Spring Boot backend for a capstone ecommerce project:

- `ProductCatalog` on port `8081`
- `UserAuth` on port `8082`
- `CartOrder` on port `8083`

The stack also includes MySQL, ZooKeeper, and Kafka for local demo flows.

## Run With Docker Compose

Prerequisites:

- Docker Desktop or Docker Engine with Compose

Start everything:

```bash
docker compose up --build
```

Services:

- Product catalog: `http://localhost:8081`
- Auth service: `http://localhost:8082`
- Cart and orders: `http://localhost:8083`
- Kafka external listener: `localhost:9094`

## Databases

One MySQL container is used with three logical databases:

- `auth_db`
- `product_db`
- `order_db`

They are created by [`docker/mysql/init/01-create-databases.sql`](/d:/workspaces/Scaler/Capstone/docker/mysql/init/01-create-databases.sql).

## Environment Variables

Each service reads runtime configuration from environment variables with local defaults.

Common values:

- `DB_HOST`
- `DB_PORT`
- `DB_NAME`
- `DB_USER`
- `DB_PASSWORD`
- `JWT_SECRET`
- `JWT_EXPIRATION_SECONDS`

Cart/order specific:

- `PRODUCT_CATALOG_BASE_URL`
- `KAFKA_BOOTSTRAP_SERVERS`
- `KAFKA_CONSUMER_GROUP_ID`
- `KAFKA_TOPIC_ORDER_CREATED`

## Demo Notes

- `ProductCatalog` seeds demo categories and products on startup.
- `UserAuth` uses Flyway for schema management.
- `CartOrder` validates JWT locally using the shared secret.
- Kafka publishes and consumes `order.created` events for demo visibility.

More detail:

- [HLD](/d:/workspaces/Scaler/Capstone/docs/HLD.md)
- [API Summary](/d:/workspaces/Scaler/Capstone/docs/API-SUMMARY.md)
- [Demo Flow](/d:/workspaces/Scaler/Capstone/docs/DEMO-FLOW.md)
