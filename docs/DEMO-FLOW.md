# Demo Flow

## 1. Start the stack

```bash
docker compose up --build
```

## 2. Create a user

```bash
curl -X POST http://localhost:8082/auth/signup \
  -H "Content-Type: application/json" \
  -d "{\"fullName\":\"Demo User\",\"email\":\"demo@example.com\",\"password\":\"password123\"}"
```

## 3. Login

```bash
curl -X POST http://localhost:8082/auth/login \
  -H "Content-Type: application/json" \
  -d "{\"email\":\"demo@example.com\",\"password\":\"password123\"}"
```

Copy the returned `accessToken`.

## 4. Browse products

```bash
curl http://localhost:8081/products
```

## 5. Add items to cart

```bash
curl -X POST http://localhost:8083/cart/items \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  -d "{\"productId\":1,\"quantity\":2}"
```

## 6. View cart

```bash
curl http://localhost:8083/cart \
  -H "Authorization: Bearer <token>"
```

## 7. Checkout

```bash
curl -X POST http://localhost:8083/checkout \
  -H "Authorization: Bearer <token>"
```

## 8. View order history

```bash
curl http://localhost:8083/orders \
  -H "Authorization: Bearer <token>"
```

## 9. Verify Kafka demo

After checkout:

- `CartOrder` publishes `order.created`
- Kafka listener logs the consumed event
- `order_event_audit` stores a simple audit record
