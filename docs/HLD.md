# High-Level Design

## Services

### ProductCatalog

- Owns product and category data
- Supports CRUD plus query capabilities for listing, filtering, and product details
- Seeds demo catalog data for local runs

### UserAuth

- Owns user accounts and authentication
- Supports signup, login, JWT issuance, and current-user lookup
- Uses Flyway for schema creation and migration

### CartOrder

- Owns carts, checkout, orders, and Kafka event publishing/consumption
- Validates JWT locally using the shared secret
- Calls `ProductCatalog` over HTTP to validate product data when cart items are added

## Data Flow

1. User signs up or logs in through `UserAuth`
2. `UserAuth` returns a JWT
3. Client sends JWT to `CartOrder`
4. `CartOrder` validates JWT locally
5. `CartOrder` calls `ProductCatalog` when adding products to cart
6. Checkout creates an order and publishes `order.created`
7. Kafka consumer logs the event and stores a simple audit row

## Storage

One MySQL container is shared for demo convenience:

- `auth_db` for auth data
- `product_db` for catalog data
- `order_db` for cart and order data

## Messaging

- Kafka topic: `order.created`
- Producer: `CartOrder` after successful checkout
- Consumer: `CartOrder` listener for logging and audit persistence
