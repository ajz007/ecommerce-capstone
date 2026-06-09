# API Summary

## Auth Service

Swagger: `http://localhost:8082/swagger-ui/index.html`

- `POST /auth/signup`
- `POST /auth/login`
- `GET /auth/me`

## Product Catalog Service

Swagger: `http://localhost:8081/swagger-ui/index.html`

- `GET /products`
- `GET /products/{id}`
- `GET /products/categories`
- `POST /products`
- `PUT /products/{id}`
- `DELETE /products/{id}`

## Cart and Order Service

Swagger: `http://localhost:8083/swagger-ui/index.html`

Cart:

- `POST /cart/items`
- `GET /cart`
- `PUT /cart/items/{itemId}`
- `DELETE /cart/items/{itemId}`
- `DELETE /cart`

Checkout and orders:

- `GET /checkout/preview`
- `POST /checkout`
- `GET /orders`
- `GET /orders/{orderId}`

## Auth Header

Protected endpoints expect:

```text
Authorization: Bearer <jwt>
```
