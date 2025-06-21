# MongoDB CheatSheet


### MongoDB version From the Terminal (MongoDB CLI):

```
mongod --version or mongosh --version
```

### Find mongo database folder on the Linux filesystem
```
grep -i dbPath /etc/mongod.conf
```

### Switch to directory
```
cd /var/lib/mongodb
```

### Go Inside the Mongo Shell to see collections
```
mongosh
```


### List All Databases

```
show dbs
```

### Show Current Database

```
db
```

### Create Or Switch Database

```
use databaseName
```

### Create Collection

```
db.createCollection('products')
```

### Show Collections

```
show collections
```
### Get All Documents in a DB

```
db.collectionName.find()
```

### Get All Documents format output nicely

```
db.collectionName.find().pretty()
```

### Find Documents

```
db.products.find({ category: 'Gadgets' })
```

### Find Documet with Partial Search

```
db.users.find({ name: /<full_or_partial_text>/i}) #(case insensitive)
```

### Insert Single Document

```
db.products.insert({
  {
    name: 'iPhone 18 pro',
    price: 200,
    quantity: 4
  }
})
```

### Insert Multiple Documents

```
db.products.insertMany([
  {
    name: 'iPhone 18 pro',
    price: 200,
    quantity: 4
  },
  {
    name: 'Samsung Pro',
    price: 150,
    quantity: 13
  },
  {
    name: 'Tesla Pi',
    price: 180,
    quantity: 7
  }
])
```


### Sort Documents

```
# asc
db.products.find().sort({ name: 1 }).pretty()
# desc
db.products.find().sort({ name: -1 }).pretty()
```

### Count Documents

```
db.products.find().count()
```

### Limit Documents

```
db.products.find().limit(2).pretty()
```

### Chaining Documents

```
db.products.find().limit(2).sort({ name: 1 }).pretty()
```

### Foreach

```
db.products.find().forEach(function(doc) {
  print("Product Name: " + doc.name)
})
```

### Find One Document

```
db.products.findOne({ category: 'Gadgets' })
```

### Update Document

```
db.products.update({ name: 'iPhone pro' },
{
  name: 'iPhine pro latest',
  price: 180,
  date: Date()
},
{
  upsert: true
})
```

### Rename Field

```
db.products.update({ name: 'iPhone pro' },
{
  $rename: {
    price: 170
  }
})
```

### Delete Document

```
db.products.remove({ name: 'iPhone pro' })
```

### Drop DB (switch to DB first with "use testDB"), then,

```
db.dropDatabase()
```

### Exit from DB
```
exit
```