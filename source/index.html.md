---
title: WebSocket API Reference
---

# WebSocket API Reference

This document describes the WebSocket API for our platform. Below you'll find the supported `Request` types that you can use.

## SearchSymbol

### Description

Searches for a symbol based on the provided pattern.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `limit`: (number) The maximum number of results.
- `pat`: (string) The search pattern.
- `scope`: (SymScope) The search scope.
- `type`: (string) Set to "SearchSymbol".

### Example JSON

```json
{
  "id": 1,
  "limit": 10,
  "pat": "AAPL",
  "scope": "some_scope",
  "type": "SearchSymbol"
}
```

---

## QueryTradableProductIndex

### Description

Queries tradable product index based on the given query.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `query`: (Query) The query to perform.
- `type`: (string) Set to "QueryTradableProductIndex".

### Example JSON

```json
{
  "id": 2,
  "query": {
    // Query Object Details
  },
  "type": "QueryTradableProductIndex"
}
```

---

## GetRouteDetails

### Description

Retrieve details for the given routes.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `route`: (RouteId[]) An array of route IDs.
- `type`: (string) Set to "GetRouteDetails".

### Example JSON

```json
{
  "id": 3,
  "route": ["route1", "route2"],
  "type": "GetRouteDetails"
}
```

---

## GetVenueDetails

### Description

Retrieve details for the given venues.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `venue`: (VenueId[]) An array of venue IDs.
- `type`: (string) Set to "GetVenueDetails".

### Example JSON

```json
{
  "id": 4,
  "venue": ["venue1", "venue2"],
  "type": "GetVenueDetails"
}
```

---

## GetProductDetails

### Description

Retrieve details for the given products.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `product`: (ProductId[]) An array of product IDs.
- `type`: (string) Set to "GetProductDetails".

### Example JSON

```json
{
  "id": 5,
  "product": ["product1", "product2"],
  "type": "GetProductDetails"
}
```

---

## GetTradableProductDetails

### Description

Retrieve details for the given tradable products.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `tradable_product`: (TradableProductId[]) An array of tradable product IDs.
- `type`: (string) Set to "GetTradableProductDetails".

### Example JSON

```json
{
  "id": 6,
  "tradable_product": ["tp1", "tp2"],
  "type": "GetTradableProductDetails"
}
```

---

## GetCanonicalTradableProduct

### Description

Retrieve the canonical tradable product for the given products.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `product`: (ProductId[]) An array of product IDs.
- `type`: (string) Set to "GetCanonicalTradableProduct".

### Example JSON

```json
{
  "id": 7,
  "product": ["product1", "product2"],
  "type": "GetCanonicalTradableProduct"
}
```

---

## SendLimitOrder

### Description

Send a limit order with the given parameters.

### Request Fields

- `account`: (Account) The account to use.
- `dir`: (Dir) The direction of the order.
- `id`: (number) Unique identifier for the request.
- `params`: (EstimateOrderParams | null) Optional order parameters.
- `price`: (Decimal) The order price.
- `quantity`: (Decimal) The order quantity.
- `quote_id`: (Str | null) Optional quote ID.
- `target`: (TradableProductId) The target tradable product.
- `type`: (string) Set to "SendLimitOrder".

### Example JSON

```json
{
  "account": "account1",
  "dir": "buy",
  "id": 8,
  "params": null,
  "price": "100.0",
  "quantity": "10.0",
  "quote_id": null,
  "target": "tp1",
  "type": "SendLimitOrder"
}
```

---

## CancelOrder

### Description

Cancel the order with the given order ID.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `order_id`: (OrderId) The ID of the order to cancel.
- `type`: (string) Set to "CancelOrder".

### Example JSON

```json
{
  "id": 9,
  "order_id": "order1",
  "type": "CancelOrder"
}
```

---

## ListOpen

### Description

List open orders based on the given scope and set.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `scope`: (LimitScope) The scope to search within.
- `set`: (LimitSet) The set to search within.
- `type`: (string) Set to "ListOpen".

### Example JSON

```json
{
  "id": 10,
  "scope": "some_scope",
  "set": "some_set",
  "type": "ListOpen"
}
```

---

## GetOrderState

### Description

Retrieve the state of orders based on the given order IDs.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `order_ids`: (OrderId[]) An array of order IDs.
- `type`: (string) Set to "GetOrderState".

### Example JSON

```json
{
  "id": 11,
  "order_ids": ["order1", "order2"],
  "type": "GetOrderState"
}
```

---

## SubscribeOrderState

### Description

Subscribe to order state updates.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `type`: (string) Set to "SubscribeOrderState".

### Example JSON

```json
{
  "id": 12,
  "type": "SubscribeOrderState"
}
```

---

## GetRejectReason

### Description

Retrieve the reason for order rejection based on the given order IDs.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `order_ids`: (OrderId[]) An array of order IDs.
- `type`: (string) Set to "GetRejectReason".

### Example JSON

```json
{
  "id": 13,
  "order_ids": ["order1", "order2"],
  "type": "GetRejectReason"
}
```

---

## GetOrderDetails

### Description

Retrieve details of orders based on the given order IDs.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `order_ids`: (OrderId[]) An array of order IDs.
- `type`: (string) Set to "GetOrderDetails".

### Example JSON

```json
{
  "id": 14,
  "order_ids": ["order1", "order2"],
  "type": "GetOrderDetails"
}
```

---

## ListFills

### Description

List fills based on the given scope and set.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `scope`: (LimitScope) The scope to search within.
- `set`: (LimitSet) The set to search within.
- `type`: (string) Set to "ListFills".

### Example JSON

```json
{
  "id": 15,
  "scope": "some_scope",
  "set": "some_set",
  "type": "ListFills"
}
```

---

## GetFillDetails

### Description

Retrieve details of fills based on the given fill IDs.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `fill_ids`: (FillId[]) An array of fill IDs.
- `type`: (string) Set to "GetFillDetails".

### Example JSON

```json
{
  "id": 16,
  "fill_ids": ["fill1", "fill2"],
  "type": "GetFillDetails"
}
```

---

## SetLimits

### Description

Set limits based on the given Limit array.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `limits`: (Limit[]) An array of Limit objects.
- `type`: (string) Set to "SetLimits".

### Example JSON

```json
{
  "id": 17,
  "limits": [
    // Limit Objects
  ],
  "type": "SetLimits"
}
```

