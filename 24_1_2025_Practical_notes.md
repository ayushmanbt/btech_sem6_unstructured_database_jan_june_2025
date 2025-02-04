# 24th January 2024 practical class notes

We can create a new database with the `use collection_name`

We learnt about the functions used to update elements -

`updateOne({query}, {update})`

`updateMany({query}, {update})`

`update({query}, {update})` (deprecated)

We can use the `$set` property to set a new filed in the document. Example -

```
db.collectionName.update({}, {$set: {age: 10}})
```

For deleting we can use the following command -

If you want to delete one document -

```
db.collectionName.deleteOne()
```

If you want to delete many document -

```
db.collectionName.deleteMany()
```

