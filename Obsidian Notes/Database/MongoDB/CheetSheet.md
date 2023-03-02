### Connect to MongoDB instance using `mongosh`

To connect with the local database on a different port, use the `--port` option:

```bash
mongosh --port 23023
```

The following connects to the remote database on `mymongodb.example.com`. it will ask you for password that you have to enter.

```bash
mongosh "mongodb://mymongodb.example.com:23023" --username shubham
```

### Add new field in multiple documents

```javascript
db.your_collection.update(
  {},
  { $set: {"new_field": 1} },
  { upsert: false, multi: true }
)
```

~~In the above example last 2 fields `false, true` specifies the `upsert` and `multi` flags.~~

**Upsert:** If set to true, creates a new document when no document matches the query criteria.

**Multi:** If set to true, updates multiple documents that meet the query criteria. If set to false, updates one document.

Add field based on condition:
```javascript
db.your_collection.update(
  { "field.some_field": "condition" },
  { $set: {"new_field": 1} },
  { upsert: false, multi: true }
)
```

### Update nested value/embeded document

Object:
```javascript
{
  _id: ObjectId("5a7e395e20a31e44e0e7e284"),
  name: "foo",
  address: { street: "123", town: "bar" }
}
```

Using [Dot Notation](http://docs.mongodb.org/manual/core/document/#dot-notation):
```javascript
db.people.update({ }, { $set: { "address.street": "Main Street" } })
```

### Rename field in collections

Rename one field

```javascript
db.collection.updateMany({}, {$rename:{"oldField":"newField"}}, { upsert: false, multi: true })
```

Rename multiple Field

```javascript
db.collection.updateMany({}, {$rename:{"old1":"new1", "old2":"new2"}}, { upsert: false, multi: true })
```

Rename Subfield

```javascript
db.collection.updateMany({}, {$rename:{"field.oldSub":"field.newSub"}}, { upsert: false, multi: true })
```

Or to just update the docs which contain the property

```javascript
db.collection.updateMany({ "field.oldSub": { $exists: true } }, {$rename:{"field.oldSub":"field.newSub"}}, { upsert: false, multi: true })
```