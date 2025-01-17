# Practical notes for 17/1/2025

We started with mongoDB

> **Did you know?**
>
> MongoDB uses the BSON data format, which is an extension to JSON. Normal JSON can have data of type string or number, but BSON supports additional data types like ObjectID, date, timestamp, binary objects etc. 

- you can install mongoDB from the official website - https://www.mongodb.com/docs/manual/administration/install-community/
- you can check if you have mongoDB installed or not using the `mongod --version` command
- today we mainly used mongo shell for interacting with mongoDB
- The hiararchy of MongoDB databases is as follows -

```
database -> collection -> document
```

So in words - documents together make a collection, a few collection makes a database. 

- We can check the available collections in a database using the following command -

```mongodb
db.collections()
```

- We can create a new collection using the follwoing command -

```mongodb
db.createCollection("name_of_the_collection")
```

(Make sure that you have no space in your mongoDB collection name)

- We can insert a document in a collection with this syntax -

```
db.collectionName.insert({
    property_name_1: value_1,
    property_name_2: value_2,
})
```

- We can use the insertMany function to insert more than one document at once -

```
db.collectionName.insertMany([{
    property_name_1: value_1,
    property_name_2: value_2,
},
{
    property_name_1: value_1,
    property_name_2: value_2,
},
{
    property_name_1: value_1,
    property_name_2: value_2,
}
])
```

- To list all the available entries in our collection we can use the `find` function

```
db.collection_name.find()
```

- we can filter elements with mathematical expressions. For example if we want to get a list of all the products with price less than 100 we will write -

```
db.collection_name.find({price: {$lt: 100}})
```

- The other available filters for us is $gt,$gte,$lte,$lt,$eq for comparing numerical values. For string values we can write the key and the corresponding value as it is, for example if we want to find all the entries with `city` as `kolkata` we can write 

```
db.collection_name.find({city: "Kolkata"})
```

- We can also use operators like `$and`, `$or`, `$not` for query logics

- We can use `findOne` to get one entry related to the query we gave

```
db.collection_name.findOne({city: "Kolkata"})
```