---
title: Architect API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - json
  - python

search: true

code_clipboard: true
---

# Introduction

This document describes the WebSocket API for our platform. Below you'll find the supported `Request` types that you can use.

## Request Types

| Type                                                        | Kind         | Category             |
| ----------------------------------------------------------- | ------------ | -------------------- |
| [SearchSymbol](#searchsymbol)                               | Query        | Symbology            |
| [QueryTradableProductIndex](#querytradableproductindex)     | Query        | Symbology            |
| [GetRouteDetails](#getroutedetails)                         | Query        | Symbology            |
| [GetVenueDetails](#getvenuedetails)                         | Query        | Symbology            |
| [GetProductDetails](#getproductdetails)                     | Query        | Symbology            |
| [GetTradableProductDetails](#gettradableproductdetails)     | Query        | Symbology            |
| [GetCanonicalTradableProduct](#getcanonicaltradableproduct) | Query        | Symbology            |
| [SendLimitOrder](#sendlimitorder)                           | Query        | Orderflow            |
| [CancelOrder](#cancelorder)                                 | Query        | Orderflow            |
| [ListOpen](#listopen)                                       | Query        | Orderflow            |
| [GetOrderState](#getorderstate)                             | Query        | Orderflow            |
| [SubscribeOrderState](#subscribeorderstate)                 | Subscription | Orderflow            |
| [GetRejectReason](#getrejectreason)                         | Query        | Orderflow            |
| [GetOrderDetails](#getorderdetails)                         | Query        | Orderflow            |
| [ListFills](#listfills)                                     | Query        | Orderflow            |
| [GetFillDetails](#getfilldetails)                           | Query        | Orderflow            |
| [SetLimits](#setlimits)                                     | Query        | Limits               |
| [GetLimits](#getlimits)                                     | Query        | Limits               |
| [GetGlobalLimits](#getgloballimits)                         | Query        | Limits               |
| [GetHalts](#gethalts)                                       | Query        | Halts                |
| [Halt](#halt)                                               | Query        | Halts                |
| [Resume](#resume)                                           | Query        | Halts                |
| [SubscribeAlerts](#subscribealerts)                         | Subscription | Alerts               |
| [GetAllowance](#getallowance)                               | Query        | DeFi                 |
| [SetAllowance](#setallowance)                               | Query        | DeFi                 |
| [GetOrderTransaction](#getordertransaction)                 | Query        | DeFi                 |
| [EstimateOrderParams](#estimateorderparams)                 | Query        | DeFi                 |
| [GetEVMAttempts](#getevmattempts)                           | Query        | DeFi                 |
| [EstimateEVMRetryParams](#estimateevmretryparams)           | Query        | DeFi                 |
| [RetryEVMTransaction](#retryevmtransaction)                 | Query        | DeFi                 |
| [GetHistoricalCandles](#gethistoricalcandles)               | Query        | Market Data          |
| [SubscribeTrades](#subscribetrades)                         | Subscription | Market Data          |
| [SubscribeBook](#subscribebook)                             | Subscription | Market Data          |
| [SubscribeCandles](#subscribecandles)                       | Subscription | Market Data          |
| [SubscribeConsolidatedBook](#subscribeconsolidatedbook)     | Subscription | Market Data          |
| [Unsubscribe](#unsubscribe)                                 | Query        | Market Data          |
| [SubscribeRfqs](#subscriberfqs)                             | Subscription | RFQs                 |
| [SendRfqs](#sendrfqs)                                       | Query        | RFQs                 |
| [ListSecrets](#listsecrets)                                 | Query        | Secrets              |
| [AddSecret](#addsecret)                                     | Query        | Secrets              |
| [DeleteSecret](#deletesecret)                               | Query        | Secrets              |
| [GetPathmap](#getpathmap)                                   | Query        | System Configuration |

# Symbology

## SearchSymbol

### Description

Searches for a symbol based on the provided pattern.

### Request Fields

| Field   | Type     | Required | Description                       |
| ------- | -------- | -------- | --------------------------------- |
| `id`    | number   | Yes      | Unique identifier for the request |
| `type`  | string   | Yes      | Set to "SearchSymbol"             |
| `limit` | number   | Yes      | The maximum number of results     |
| `pat`   | string   | Yes      | The search pattern                |
| `scope` | SymScope | Yes      | The search scope                  |

```json
{
  "id": 1,
  "limit": 10,
  "pat": "BTC",
  "scope": "All",
  "type": "SearchSymbol"
}
```

```python
async def main():
    client = Client()
    await client.connect()
    res = await client.query({
      "id": 1,
      "type": "SearchSymbol",
      "limit": 10,
      "pat": "BTC",
      "scope": "All"
    })
    print(res)
```

## QueryTradableProductIndex

### Description

Fast query for Tradable Product IDs that match the given query, which can be a boolean expression.

### Request Fields

| Field   | Type   | Required | Description                        |
| ------- | ------ | -------- | ---------------------------------- |
| `id`    | number | Yes      | Unique identifier for the request  |
| `type`  | string | Yes      | Set to "QueryTradableProductIndex" |
| `query` | string | Yes      | See Query type                     |

```json
{
  "id": 2,
  "query": {
    // Query Object Details
  },
  "type": "QueryTradableProductIndex"
}
```

```python
async def main():
    client = Client()
    await client.connect()
    res = await client.query({
      "id": 1,
      "type": "QueryTradableProductIndex",
      "Query": "..."
    })
    print(res)
```

## GetRouteDetails

### Description

Retrieve details for the given routes.

### Request Fields

| Field   | Type     | Required | Description                       |
| ------- | -------- | -------- | --------------------------------- |
| `id`    | number   | Yes      | Unique identifier for the request |
| `type`  | string   | Yes      | Set to "GetRouteDetails"          |
| `route` | string[] | Yes      | An array of route IDs             |

```json
{
  "id": 3,
  "route": ["route1", "route2"],
  "type": "GetRouteDetails"
}
```

## GetVenueDetails

### Description

Retrieve details for the given venues.

### Request Fields

| Field   | Type     | Required | Description                       |
| ------- | -------- | -------- | --------------------------------- |
| `id`    | number   | Yes      | Unique identifier for the request |
| `type`  | string   | Yes      | Set to "GetVenueDetails"          |
| `venue` | string[] | Yes      | An array of venue IDs             |

```json
{
  "id": 4,
  "venue": ["venue1", "venue2"],
  "type": "GetVenueDetails"
}
```

## GetProductDetails

### Description

Retrieve details for the given products.

### Request Fields

| Field     | Type     | Required | Description                       |
| --------- | -------- | -------- | --------------------------------- |
| `id`      | number   | Yes      | Unique identifier for the request |
| `type`    | string   | Yes      | Set to "GetProductDetails"        |
| `product` | string[] | Yes      | An array of product IDs           |

```json
{
  "id": 5,
  "product": ["product1", "product2"],
  "type": "GetProductDetails"
}
```

## GetTradableProductDetails

### Description

Retrieve details for the given tradable products.

### Request Fields

| Field              | Type     | Required | Description                        |
| ------------------ | -------- | -------- | ---------------------------------- |
| `id`               | number   | Yes      | Unique identifier for the request  |
| `type`             | string   | Yes      | Set to "GetTradableProductDetails" |
| `tradable_product` | string[] | Yes      | An array of tradable product IDs   |

```json
{
  "id": 6,
  "tradable_product": ["tp1", "tp2"],
  "type": "GetTradableProductDetails"
}
```

## GetCanonicalTradableProduct

### Description

Retrieve the canonical tradable product for the given products. A canonical tradable product is an example \*/USD or \*/USDC or \*/USDT pair on a liquid exchange that we support.

### Request Fields

| Field     | Type     | Required | Description                          |
| --------- | -------- | -------- | ------------------------------------ |
| `id`      | number   | Yes      | Unique identifier for the request    |
| `type`    | string   | Yes      | Set to "GetCanonicalTradableProduct" |
| `product` | string[] | Yes      | An array of product IDs              |

```json
{
  "id": 7,
  "product": ["product1", "product2"],
  "type": "GetCanonicalTradableProduct"
}
```

# Orderflow

## SendLimitOrder

### Description

Send a limit order with the given parameters.

### Request Fields

| Field      | Type                | Required | Description                                   |
| ---------- | ------------------- | -------- | --------------------------------------------- |
| `id`       | number              | Yes      | Unique identifier for the request             |
| `type`     | string              | Yes      | Set to "SendLimitOrder"                       |
| `target`   | string              | Yes      | Tradable product ID                           |
| `dir`      | Dir                 | Yes      | The direction of the order ("Buy" or "Sell")  |
| `id`       | number              | Yes      | Unique identifier for the request             |
| `price`    | Decimal             | Yes      | The order price                               |
| `quantity` | Decimal             | Yes      | The order quantity                            |
| `account`  | string              | Yes      | The account to use (usually "DEFAULT")        |
| `quote_id` | Str                 | No       | Optional quote ID if responding to a firm RFQ |
| `params`   | EstimateOrderParams | No       | Optional order parameters (e.g. for DeFi).    |

```json
{
  "id": 8,
  "type": "SendLimitOrder",
  "target": "tp1",
  "dir": "Buy",
  "price": "100.0",
  "quantity": "10.0",
  "account": "DEFAULT"
}
```

## CancelOrder

### Description

Cancel the order with the given order ID.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `order_id`: (OrderId) The ID of the order to cancel.
- `type`: (string) Set to "CancelOrder".

```json
{
  "id": 9,
  "order_id": "order1",
  "type": "CancelOrder"
}
```

## ListOpen

### Description

List open orders based on the given scope and set.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `scope`: (LimitScope) The scope to search within.
- `set`: (LimitSet) The set to search within.
- `type`: (string) Set to "ListOpen".

```json
{
  "id": 10,
  "scope": "some_scope",
  "set": "some_set",
  "type": "ListOpen"
}
```

## GetOrderState

### Description

Retrieve the state of orders based on the given order IDs.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `order_ids`: (OrderId[]) An array of order IDs.
- `type`: (string) Set to "GetOrderState".

```json
{
  "id": 11,
  "order_ids": ["order1", "order2"],
  "type": "GetOrderState"
}
```

## SubscribeOrderState

### Description

Subscribe to order state updates.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `type`: (string) Set to "SubscribeOrderState".

```json
{
  "id": 12,
  "type": "SubscribeOrderState"
}
```

## GetRejectReason

### Description

Retrieve the reason for order rejection based on the given order IDs.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `order_ids`: (OrderId[]) An array of order IDs.
- `type`: (string) Set to "GetRejectReason".

```json
{
  "id": 13,
  "order_ids": ["order1", "order2"],
  "type": "GetRejectReason"
}
```

## GetOrderDetails

### Description

Retrieve details of orders based on the given order IDs.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `order_ids`: (OrderId[]) An array of order IDs.
- `type`: (string) Set to "GetOrderDetails".

```json
{
  "id": 14,
  "order_ids": ["order1", "order2"],
  "type": "GetOrderDetails"
}
```

## ListFills

### Description

List fills based on the given scope and set.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `scope`: (LimitScope) The scope to search within.
- `set`: (LimitSet) The set to search within.
- `type`: (string) Set to "ListFills".

```json
{
  "id": 15,
  "scope": "some_scope",
  "set": "some_set",
  "type": "ListFills"
}
```

## GetFillDetails

### Description

Retrieve details of fills based on the given fill IDs.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `fill_ids`: (FillId[]) An array of fill IDs.
- `type`: (string) Set to "GetFillDetails".

```json
{
  "id": 16,
  "fill_ids": ["fill1", "fill2"],
  "type": "GetFillDetails"
}
```

# Limits

## SetLimits

### Description

Set limits based on the given Limit array.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `limits`: (Limit[]) An array of Limit objects.
- `type`: (string) Set to "SetLimits".

```json
{
  "id": 17,
  "limits": [
    // Limit Objects
  ],
  "type": "SetLimits"
}
```

## GetLimits

### Description

Retrieve limits based on the given LimitSet and LimitScope arrays.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `limits`: ([LimitSet, LimitScope][]) An array of pairs containing LimitSet and LimitScope.
- `type`: (string) Set to "GetLimits".

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

## GetGlobalLimits

### Description

Retrieve global limits based on the given GlobalLimitName array.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `limits`: (GlobalLimitName[]) An array of global limit names.
- `type`: (string) Set to "GetGlobalLimits".

```json
{
  "id": 19,
  "limits": ["limit1", "limit2"],
  "type": "GetGlobalLimits"
}
```

# Halts

## GetHalts

### Description

Retrieve information about trading halts.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `type`: (string) Set to "GetHalts".

```json
{
  "id": 20,
  "type": "GetHalts"
}
```

## Halt

### Description

Initiate a trading halt for a given condition.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `halt`: (Halt) The condition for initiating the halt.
- `type`: (string) Set to "Halt".

```json
{
  "id": 21,
  "halt": "condition",
  "type": "Halt"
}
```

## Resume

### Description

Resume trading after a halt for a given condition.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `resume`: (Halt) The condition for resuming trading.
- `type`: (string) Set to "Resume".

```json
{
  "id": 22,
  "resume": "condition",
  "type": "Resume"
}
```

# Alerts

## SubscribeAlerts

### Description

Subscribe to alerts based on the given path and seek string.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `path`: (string) The path for alerts.
- `seek`: (string) The seek string.
- `type`: (string) Set to "SubscribeAlerts".

```json
{
  "id": 24,
  "path": "some/path",
  "seek": "seek_string",
  "type": "SubscribeAlerts"
}
```

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

## GetOrderTransaction

### Description

Get transaction information for given order IDs.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `order_ids`: (OrderId[]) Array of Order IDs.
- `type`: (string) Set to "GetOrderTransaction".

```json
{
  "id": 38,
  "order_ids": ["order_1", "order_2"],
  "type": "GetOrderTransaction"
}
```

## EstimateOrderParams

### Description

Estimate order parameters based on an order prototype.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `order`: (OrderPrototype) Prototype of the order.
- `type`: (string) Set to "EstimateOrderParams".

```json
{
"id": 39,
"order": {...},
"type": "EstimateOrderParams"
}
```

## GetEVMAttempts

### Description

Get the attempts for an EVM transaction.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `transaction`: (TransactionHandle) Handle for the transaction.
- `type`: (string) Set to "GetEVMAttempts".

```json
{
  "id": 40,
  "transaction": "txn_1234",
  "type": "GetEVMAttempts"
}
```

## EstimateEVMRetryParams

### Description

Estimate retry parameters for an EVM transaction.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `transaction`: (TransactionHandle) Handle for the transaction.
- `type`: (string) Set to "EstimateEVMRetryParams".

```json
{
  "id": 41,
  "transaction": "txn_1234",
  "type": "EstimateEVMRetryParams"
}
```

## RetryEVMTransaction

### Description

Retry an EVM transaction with optional gas parameters.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `transaction`: (TransactionHandle) Handle for the transaction.
- `gas`: (number|null) Gas amount (optional).
- `gas_price`: ([number, number]|null) Gas price range (optional).
- `type`: (string) Set to "RetryEVMTransaction".

```json
{
  "id": 42,
  "transaction": "txn_1234",
  "gas": 50000,
  "gas_price": [20, 30],
  "type": "RetryEVMTransaction"
}
```

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

## SubscribeTrades

### Description

Subscribe to trades for a given tradable product.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `tradable_product`: (TradableProductId) Tradable Product ID.
- `type`: (string) Set to "SubscribeTrades".

```json
{
  "id": 28,
  "tradable_product": "product_id",
  "type": "SubscribeTrades"
}
```

## SubscribeBook

### Description

Subscribe to the order book for a given tradable product and width.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `tradable_product`: (TradableProductId) Tradable Product ID.
- `width`: (number) Width.
- `type`: (string) Set to "SubscribeBook".

```json
{
  "id": 29,
  "tradable_product": "product_id",
  "width": 10,
  "type": "SubscribeBook"
}
```

## SubscribeCandles

### Description

Subscribe to candles for a given tradable product and width.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `tradable_product`: (TradableProductId) Tradable Product ID.
- `width`: (CandleWidth) Width.
- `type`: (string) Set to "SubscribeCandles".

```json
{
  "id": 32,
  "tradable_product": "product_id",
  "width": "1h",
  "type": "SubscribeCandles"
}
```

## SubscribeConsolidatedBook

### Description

Subscribe to the consolidated book for given tradable products with specified precision.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `tradable_products`: (TradableProductId[]) An array of Tradable Product IDs.
- `precision`: (Decimal) Precision.
- `type`: (string) Set to "SubscribeConsolidatedBook".

```json
{
  "id": 30,
  "tradable_products": ["product_id1", "product_id2"],
  "precision": "0.01",
  "type": "SubscribeConsolidatedBook"
}
```

## Unsubscribe

### Description

Unsubscribe from previous subscriptions.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `type`: (string) Set to "Unsubscribe".

```json
{
  "id": 33,
  "type": "Unsubscribe"
}
```

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

## SendRfqs

### Description

Send request for quotes based on a query.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `query`: (SendRfqsQuery) Query for RFQs.
- `type`: (string) Set to "SendRfqs".

```json
{
"id": 43,
"query": {...},
"type": "SendRfqs"
}
```

## Unsubscribe

### Description

Unsubscribe from previous subscriptions.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `type`: (string) Set to "Unsubscribe".

```json
{
  "id": 33,
  "type": "Unsubscribe"
}
```

# Secrets

## ListSecrets

### Description

List all secrets.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `type`: (string) Set to "ListSecrets".

```json
{
  "id": 35,
  "type": "ListSecrets"
}
```

## AddSecret

### Description

Add a secret with a given key and value.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `secret_key`: (SecretKey) Secret key.
- `value`: (number[]) An array of numerical values.
- `type`: (string) Set to "AddSecret".

```json
{
  "id": 36,
  "secret_key": "my_secret_key",
  "value": [1, 2, 3],
  "type": "AddSecret"
}
```

## DeleteSecret

### Description

Delete a secret with a given key.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `secret_key`: (SecretKey) Secret key.
- `type`: (string) Set to "DeleteSecret".

```json
{
  "id": 37,
  "secret_key": "my_secret_key",
  "type": "DeleteSecret"
}
```

# System Configuration

## GetPathmap

### Description

Retrieve the pathmap.

### Request Fields

- `id`: (number) Unique identifier for the request.
- `type`: (string) Set to "GetPathmap".

```json
{
  "id": 34,
  "type": "GetPathmap"
}
```
