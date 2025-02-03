# 30/1/2025 class notes

**MongoDB Updates and Nested Update Queries**

### 1. Updating Documents in MongoDB
MongoDB provides various update operators to modify documents in a collection. The most common ones include:
- `$set`: Adds new fields or updates existing ones.
- `$unset`: Removes a field from a document.
- `$inc`: Increments or decrements a numeric field.
- `$mul`: Multiplies the value of a field by a given factor.
- `$rename`: Renames a field.

### 2. Adding New Fields Using `$set`
You can add new fields to a document using the `$set` operator. If the field does not exist, it is created.

#### Example:
```javascript
// Sample document
{
  _id: ObjectId("654321"),
  name: "John",
  age: 25
}

// Add a new field 'address'
db.users.updateOne(
  { _id: ObjectId("654321") },
  { $set: { address: "New York" } }
);
```

**Resulting document:**
```json
{
  "_id": ObjectId("654321"),
  "name": "John",
  "age": 25,
  "address": "New York"
}
```

### 3. Updating Field Values
MongoDB provides various mathematical operators for updating numeric values:

- **`$inc`**: Increments or decrements a numeric field.
- **`$mul`**: Multiplies the field value.
- **`$add` (Array operator)**: Adds elements to an array.
- **`$subtract` (Aggregation only)**: Subtracts values.

#### Example: Incrementing Age by 1
```javascript
db.users.updateOne(
  { _id: ObjectId("654321") },
  { $inc: { age: 1 } }
);
```

#### Example: Multiplying a Salary Field
```javascript
db.employees.updateOne(
  { _id: ObjectId("123456") },
  { $mul: { salary: 1.1 } } // Increases salary by 10%
);
```

#### Example: Multiple updates together
```js
db.collection.updateMany({}, { 
  $set: { salary: { $add: [{ $multiply: ["$salary", 1.5] }, 120] } } 
})
```

### 4. Nested Updates
Updating fields within embedded documents requires using the dot (`.`) notation.

#### Example: Updating a Nested Field
```javascript
// Sample document
{
  _id: ObjectId("654321"),
  name: "John",
  contact: {
    phone: "1234567890",
    email: "john@example.com"
  }
}

// Update nested field 'contact.phone'
db.users.updateOne(
  { _id: ObjectId("654321") },
  { $set: { "contact.phone": "0987654321" } }
);
```

**Resulting document:**
```json
{
  "_id": ObjectId("654321"),
  "name": "John",
  "contact": {
    "phone": "0987654321",
    "email": "john@example.com"
  }
}
```


### Conclusion
MongoDB provides powerful update operators to modify documents efficiently. Using `$set`, `$inc`, `$mul`, and nested updates, developers can manipulate data with flexibility while ensuring atomic updates.
