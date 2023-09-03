---
title: WebSocket API Reference
---

# Introduction

This document describes the WebSocket API for our platform. Below you'll find the supported `Request` types that you can use.

# Symbology

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

# Orderflow

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

# Limits

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

---

## GetLimits

### Description

Retrieve limits based on the given LimitSet and LimitScope arrays.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `limits`: ([LimitSet, LimitScope][]) An array of pairs containing LimitSet and LimitScope.
- `type`: (string) Set to "GetLimits".

### Example JSON

```json
{
  "id": 18,
  "limits": [
    ["set1", "scope1"],
    ["set2", "scope2"]
  ],
  "type": "GetLimits"
}
```

---

## GetGlobalLimits

### Description

Retrieve global limits based on the given GlobalLimitName array.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `limits`: (GlobalLimitName[]) An array of global limit names.
- `type`: (string) Set to "GetGlobalLimits".

### Example JSON

```json
{
  "id": 19,
  "limits": ["limit1", "limit2"],
  "type": "GetGlobalLimits"
}
```

---

# Halts

## GetHalts

### Description

Retrieve information about trading halts.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `type`: (string) Set to "GetHalts".

### Example JSON

```json
{
  "id": 20,
  "type": "GetHalts"
}
```

---

## Halt

### Description

Initiate a trading halt for a given condition.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `halt`: (Halt) The condition for initiating the halt.
- `type`: (string) Set to "Halt".

### Example JSON

```json
{
  "id": 21,
  "halt": "condition",
  "type": "Halt"
}
```

---

## Resume

### Description

Resume trading after a halt for a given condition.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `resume`: (Halt) The condition for resuming trading.
- `type`: (string) Set to "Resume".

### Example JSON

```json
{
  "id": 22,
  "resume": "condition",
  "type": "Resume"
}
```

---

# Alerts

## SubscribeAlerts

### Description

Subscribe to alerts based on the given path and seek string.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `path`: (string) The path for alerts.
- `seek`: (string) The seek string.
- `type`: (string) Set to "SubscribeAlerts".

### Example JSON

```json
{
  "id": 24,
  "path": "some/path",
  "seek": "seek_string",
  "type": "SubscribeAlerts"
}
```

---

# DeFi

## GetAllowance

### Description

Retrieve allowance based on the given account, route, token, and venue.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `account`: (Account) Account information.
- `route`: (RouteId) Route ID.
- `token`: (ProductId) Token ID.
- `venue`: (VenueId) Venue ID.
- `type`: (string) Set to "GetAllowance".

### Example JSON

```json
{
  "id": 25,
  "account": "account_info",
  "route": "route_id",
  "token": "token_id",
  "venue": "venue_id",
  "type": "GetAllowance"
}
```

---

## SetAllowance

### Description

Set allowance based on the given account, route, amount, token, and venue.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `account`: (Account) Account information.
- `route`: (RouteId) Route ID.
- `amount`: (Decimal) Amount.
- `token`: (ProductId) Token ID.
- `venue`: (VenueId) Venue ID.
- `type`: (string) Set to "SetAllowance".

### Example JSON

```json
{
  "id": 26,
  "account": "account_info",
  "route": "route_id",
  "amount": "100",
  "token": "token_id",
  "venue": "venue_id",
  "type": "SetAllowance"
}
```

---

## GetOrderTransaction

### Description

Get transaction information for given order IDs.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `order_ids`: (OrderId[]) Array of Order IDs.
- `type`: (string) Set to "GetOrderTransaction".

### Example JSON

```json
{
  "id": 38,
  "order_ids": ["order_1", "order_2"],
  "type": "GetOrderTransaction"
}
```

---

## EstimateOrderParams

### Description

Estimate order parameters based on an order prototype.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `order`: (OrderPrototype) Prototype of the order.
- `type`: (string) Set to "EstimateOrderParams".

### Example JSON

```json
{
"id": 39,
"order": {...},
"type": "EstimateOrderParams"
}
```

---

## GetEVMAttempts

### Description

Get the attempts for an EVM transaction.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `transaction`: (TransactionHandle) Handle for the transaction.
- `type`: (string) Set to "GetEVMAttempts".

### Example JSON

```json
{
  "id": 40,
  "transaction": "txn_1234",
  "type": "GetEVMAttempts"
}
```

---

## EstimateEVMRetryParams

### Description

Estimate retry parameters for an EVM transaction.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `transaction`: (TransactionHandle) Handle for the transaction.
- `type`: (string) Set to "EstimateEVMRetryParams".

### Example JSON

```json
{
  "id": 41,
  "transaction": "txn_1234",
  "type": "EstimateEVMRetryParams"
}
```

---

## RetryEVMTransaction

### Description

Retry an EVM transaction with optional gas parameters.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `transaction`: (TransactionHandle) Handle for the transaction.
- `gas`: (number|null) Gas amount (optional).
- `gas_price`: ([number, number]|null) Gas price range (optional).
- `type`: (string) Set to "RetryEVMTransaction".

### Example JSON

```json
{
  "id": 42,
  "transaction": "txn_1234",
  "gas": 50000,
  "gas_price": [20, 30],
  "type": "RetryEVMTransaction"
}
```

---

# Market Data

## GetHistoricalCandles

### Description

Retrieve historical candle data based on the given tradable product, start time, end time, and width.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `start`: (string) Start time.
- `end`: (string) End time.
- `tradable_product`: (TradableProductId) Tradable Product ID.
- `width`: (CandleWidth) Width.
- `type`: (string) Set to "GetHistoricalCandles".

### Example JSON

```json
{
  "id": 27,
  "start": "2021-01-01T00:00:00Z",
  "end": "2021-01-02T00:00:00Z",
  "tradable_product": "product_id",
  "width": "1h",
  "type": "GetHistoricalCandles"
}
```

---

## SubscribeTrades

### Description

Subscribe to trades for a given tradable product.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `tradable_product`: (TradableProductId) Tradable Product ID.
- `type`: (string) Set to "SubscribeTrades".

### Example JSON

```json
{
  "id": 28,
  "tradable_product": "product_id",
  "type": "SubscribeTrades"
}
```

---

## SubscribeBook

### Description

Subscribe to the order book for a given tradable product and width.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `tradable_product`: (TradableProductId) Tradable Product ID.
- `width`: (number) Width.
- `type`: (string) Set to "SubscribeBook".

### Example JSON

```json
{
  "id": 29,
  "tradable_product": "product_id",
  "width": 10,
  "type": "SubscribeBook"
}
```

---

## SubscribeCandles

### Description

Subscribe to candles for a given tradable product and width.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `tradable_product`: (TradableProductId) Tradable Product ID.
- `width`: (CandleWidth) Width.
- `type`: (string) Set to "SubscribeCandles".

### Example JSON

```json
{
  "id": 32,
  "tradable_product": "product_id",
  "width": "1h",
  "type": "SubscribeCandles"
}
```

---

## SubscribeConsolidatedBook

### Description

Subscribe to the consolidated book for given tradable products with specified precision.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `tradable_products`: (TradableProductId[]) An array of Tradable Product IDs.
- `precision`: (Decimal) Precision.
- `type`: (string) Set to "SubscribeConsolidatedBook".

### Example JSON

```json
{
  "id": 30,
  "tradable_products": ["product_id1", "product_id2"],
  "precision": "0.01",
  "type": "SubscribeConsolidatedBook"
}
```

---

## Unsubscribe

### Description

Unsubscribe from previous subscriptions.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `type`: (string) Set to "Unsubscribe".

### Example JSON

```json
{
  "id": 33,
  "type": "Unsubscribe"
}
```

---

# RFQs

## SubscribeRfqs

### Description

Subscribe to RFQs for given base and quote products, quantity, and venues.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `base`: (ProductId) Base Product ID.
- `quote`: (ProductId) Quote Product ID.
- `quantity`: (Decimal) Quantity.
- `venues`: (VenueId[]) An array of Venue IDs.
- `type`: (string) Set to "SubscribeRfqs".

### Example JSON

```json
{
  "id": 31,
  "base": "base_product",
  "quote": "quote_product",
  "quantity": "10",
  "venues": ["venue1", "venue2"],
  "type": "SubscribeRfqs"
}
```

---

## SendRfqs

### Description

Send request for quotes based on a query.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `query`: (SendRfqsQuery) Query for RFQs.
- `type`: (string) Set to "SendRfqs".

### Example JSON

```json
{
"id": 43,
"query": {...},
"type": "SendRfqs"
}
```

---

## Unsubscribe

### Description

Unsubscribe from previous subscriptions.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `type`: (string) Set to "Unsubscribe".

### Example JSON

```json
{
  "id": 33,
  "type": "Unsubscribe"
}
```

---

# Secrets

## ListSecrets

### Description

List all secrets.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `type`: (string) Set to "ListSecrets".

### Example JSON

```json
{
  "id": 35,
  "type": "ListSecrets"
}
```

---

## AddSecret

### Description

Add a secret with a given key and value.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `secret_key`: (SecretKey) Secret key.
- `value`: (number[]) An array of numerical values.
- `type`: (string) Set to "AddSecret".

### Example JSON

```json
{
  "id": 36,
  "secret_key": "my_secret_key",
  "value": [1, 2, 3],
  "type": "AddSecret"
}
```

---

## DeleteSecret

### Description

Delete a secret with a given key.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `secret_key`: (SecretKey) Secret key.
- `type`: (string) Set to "DeleteSecret".

### Example JSON

```json
{
  "id": 37,
  "secret_key": "my_secret_key",
  "type": "DeleteSecret"
}
```

---

# System Configuration

## GetPathmap

### Description

Retrieve the pathmap.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `type`: (string) Set to "GetPathmap".

### Example JSON

```json
{
  "id": 34,
  "type": "GetPathmap"
}
```

---
