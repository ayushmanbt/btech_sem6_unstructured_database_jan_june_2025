# 24th January 2024 practical class notes

We learnt about the functions used to update elements -

`updateOne({query}, {update})`

`updateMany({query}, {update})`

`update({query}, {update})` (deprecated)

We can use the `$set` property to set a new filed in the document. Example -

```
db.collectionName.update({}, {$set: {age: 10}})
```