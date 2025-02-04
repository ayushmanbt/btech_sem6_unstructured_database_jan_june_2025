# Class notes for 4/2/2025

MongoDB's aggregation framework is a powerful tool used to process and analyze data within a collection. It allows you to perform complex transformations and computations on documents, similar to SQL's GROUP BY and JOIN operations.

## $group

group can be used to group by certain fields

Example Collection: orders

```json
[
  { "_id": 1, "product": "Laptop", "category": "Electronics", "price": 1000 },
  { "_id": 2, "product": "Phone", "category": "Electronics", "price": 500 },
  { "_id": 3, "product": "Shirt", "category": "Clothing", "price": 50 }
]
```

Find total price per category

```js
db.orders.aggregate([
  { $group: { _id: "$category", totalSales: { $sum: "$price" } } }
])
```

Count categorywise
```js
db.orders.aggregate([
  { $group: { _id: "$category", totalSales: { $sum: "$price" }, totalCount: {$sum: 1}} }
])
```

## $match

match can be used to do a normal query like `findMany()`

We can use `$match` in combination with `$group` to make filtered groups

Example of match:

```js
db.orders.aggregate([
  { $match: { category: "Electronics" } }
])
```

## $count

can be used for total counts -

```js
db.orders.aggregate([
  { $count: "totalDocuments" }
])
```

## $lookup

`$lookup` works same as join.

```json
{
  $lookup: {
    from: "otherCollection",
    localField: "fieldInCurrentCollection",
    foreignField: "fieldInOtherCollection",
    as: "resultField"
  }
}
```

### Example

**Collection 1: orderes**

```json
{ "_id": 1, "customer_id": 101, "product": "Laptop" }
{ "_id": 2, "customer_id": 102, "product": "Phone" }
```

**Collection 2: customers**

```json
{ "_id": 101, "name": "Alice", "city": "New York" }
{ "_id": 102, "name": "Bob", "city": "Los Angeles" }
```

**Query to join orders with customers**
```js
db.orders.aggregate([
  {
    $lookup: {
      from: "customers",      // Collection to join
      localField: "customer_id",  // Field in orders
      foreignField: "_id",        // Field in customers
      as: "customerDetails"       // Output array field
    }
  }
]);
```

**Output:**

```json
{
  "_id": 1,
  "customer_id": 101,
  "product": "Laptop",
  "customerDetails": [
    { "_id": 101, "name": "Alice", "city": "New York" }
  ]
}
{
  "_id": 2,
  "customer_id": 102,
  "product": "Phone",
  "customerDetails": [
    { "_id": 102, "name": "Bob", "city": "Los Angeles" }
  ]
}
```