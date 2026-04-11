# API Summary

## Auth Service

Base URL: `http://localhost:8082`

- `POST /auth/signup`
- `POST /auth/login`
- `GET /auth/me`

## Product Catalog Service

Base URL: `http://localhost:8081`

- `GET /products`
- `GET /products/{id}`
- `GET /products/categories`
- `POST /products`
- `PUT /products/{id}`
- `DELETE /products/{id}`

## Cart and Order Service

Base URL: `http://localhost:8083`

Cart:

- `POST /cart/items`
- `GET /cart`
- `PUT /cart/items/{itemId}`
- `DELETE /cart/items/{itemId}`
- `DELETE /cart`

Checkout and orders:

- `POST /checkout`
- `GET /orders`
- `GET /orders/{orderId}`

## Auth Header

Protected endpoints expect:

```text
Authorization: Bearer <jwt>
```
