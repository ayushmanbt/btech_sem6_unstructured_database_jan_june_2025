# 28/1/2025 class notes

**MongoDB Query Operators: `$and`, `$or`, `$gt`, `$gte`, `$lt`, `$lte`, `$in`, and `$all`**

MongoDB provides various query operators to filter documents based on conditions. This class note will cover logical operators `$and` and `$or`, mathematical comparison operators (`$gt`, `$gte`, `$lt`, `$lte`), the `$in` directive, and matching arrays using `$all`.

---

## **1. Logical Operators**
### **`$and` Operator**
- The `$and` operator is used to combine multiple conditions, ensuring that all specified conditions must be true.
- It is explicitly used when multiple conditions need to be combined within an array.

**Example:** Find documents where `age` is greater than 25 **AND** `city` is `"New York"`.
```javascript
 db.users.find({
     $and: [
         { age: { $gt: 25 } },
         { city: "New York" }
     ]
 })
```
*Equivalent shorthand query:* If multiple conditions are specified at the same level, MongoDB automatically applies `$and`.
```javascript
 db.users.find({ age: { $gt: 25 }, city: "New York" })
```

### **`$or` Operator**
- The `$or` operator allows at least one of the conditions to be true.
- It is used when filtering documents that satisfy one or more conditions.

**Example:** Find users who are either older than 25 **OR** live in `"New York"`.
```javascript
 db.users.find({
     $or: [
         { age: { $gt: 25 } },
         { city: "New York" }
     ]
 })
```

---

## **2. Mathematical Comparison Operators**
MongoDB provides comparison operators to filter numeric values.

| Operator | Description |
|----------|-------------|
| `$gt`  | Greater than |
| `$gte` | Greater than or equal to |
| `$lt`  | Less than |
| `$lte` | Less than or equal to |

### **Examples**
**Find users older than 30:**
```javascript
 db.users.find({ age: { $gt: 30 } })
```

**Find users aged 30 or older:**
```javascript
 db.users.find({ age: { $gte: 30 } })
```

**Find users younger than 25:**
```javascript
 db.users.find({ age: { $lt: 25 } })
```

**Find users aged 25 or younger:**
```javascript
 db.users.find({ age: { $lte: 25 } })
```

---

## **3. `$in` Operator**
- The `$in` operator is used to match any value from a given list.
- Useful when filtering documents that contain specific values in a field.

**Example:** Find users whose city is either `"New York"`, `"Los Angeles"`, or `"Chicago"`.
```javascript
 db.users.find({ city: { $in: ["New York", "Los Angeles", "Chicago"] } })
```

---

## **4. `$all` Operator**
- The `$all` operator is used to match an array field that contains all specified values.
- It ensures that all given elements exist within the array, but they may be in any order.

**Example:** Find users who have both `"MongoDB"` and `"Node.js"` in their `skills` array.
```javascript
 db.users.find({ skills: { $all: ["MongoDB", "Node.js"] } })
```

---

## MongoDB query filters

**.sort():**
The `.sort()` method is used to order the results of a query based on a specified field. You can specify ascending or descending order by passing an object where the key is the field name and the value is:

1 for ascending order.
-1 for descending order.

Example:

```js
db.collection.find().sort({ age: 1 })  // Sort by age in ascending order
db.collection.find().sort({ age: -1 }) // Sort by age in descending order
```

**.skip():**
The `.skip()` method is used to skip a specified number of documents from the beginning of the result set. This is often used for pagination purposes.

Example:

```js
db.collection.find().skip(5)  // Skip the first 5 documents
```

You can use `.skip()` in combination with .limit() to paginate your results.

**.limit():**
The `.limit()` method is used to limit the number of documents returned by a query. It's useful for restricting the result set, such as when displaying results in smaller chunks or pages.

Example:

```js
db.collection.find().limit(5)  // Return only the first 5 documents
```

When combined with .skip(), .limit() can be used to fetch specific "pages" of results.

#### Combining .sort(), .skip(), and .limit():
These methods can be chained together to control how data is returned from the database. This is especially useful for tasks like sorting, pagination, or limiting the number of results.

Example: Sorting and Pagination

If you want to retrieve the second page of results (5 items per page, sorted by age), you can combine `.sort()`, `.skip()`, and `.limit()`:

```js
db.collection.find()
  .sort({ age: 1 })   // Sort by age in ascending order
  .skip(5)            // Skip the first 5 documents (Page 1)
  .limit(5);          // Limit the result to 5 documents (Page 2)
```

---

## **Summary**
- `$and`: Ensures all conditions are true.
- `$or`: Ensures at least one condition is true.
- `$gt`, `$gte`, `$lt`, `$lte`: Used for numerical comparisons.
- `$in`: Matches any value from a given list.
- `$all`: Ensures an array contains all specified values.

These operators are fundamental in MongoDB queries, helping filter and retrieve documents efficiently.

